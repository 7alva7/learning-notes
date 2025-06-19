## Callout from Scheduled Apex not supported

```java
global class Ipv4GlobalSyncNewRegistrationsHandler implements Schedulable {
    global void execute(SchedulableContext SC) {
      // 不能在定时任务中访问外部系统: 以下代码访问了后台接口
      String accessToken = Ipv4GlobalGraphQLAPI.getAccessToken(userName, password, clientId);
   }
}
```

## You have uncommitted work pending. Please commit or rollback before calling out

```java
public class Ipv4GlobalSyncNewRegistrations {
  @future(callout=true)
  public static void sync() {
    String userName = Ipv4GlobalCustomSettings.getAuthUserName();
    String password = Ipv4GlobalCustomSettings.getAuthPassword();
    String clientId = Ipv4GlobalCustomSettings.getClientId();
    String accessToken = Ipv4GlobalGraphQLAPI.getAccessToken(userName, password, clientId);
    
    // 错误：这两个函数里面有callout，并且都会修改数据库，所以不能在同一个事务中调用
    // Ipv4GlobalLeadManager.checkAndUpdateIsEmailConfirmedForRecentLeads(accessToken);
    // Ipv4GlobalLeadManager.getInactiveEmployees(accessToken);

    // 修改为：所有callout都放在上面，所有修改数据库的操作放在下面
    String accessToken = Ipv4GlobalGraphQLAPI.getAccessToken(userName, password, clientId);
    List<Ipv4GlobalEmployee> employees = Ipv4GlobalGraphQLAPI.getInactiveEmployees(accessToken, 0 , queryLimit);
    // 这里也会有 callout，但在这之前没有任何数据库操作，所以不会报错
    Ipv4GlobalLeadManager.checkAndUpdateIsEmailConfirmedForRecentLeads(accessToken);
    Ipv4GlobalLeadManager.createLeadsIfNeeded(employees);
  }
}
```