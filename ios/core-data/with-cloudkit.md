# Integrating Core Data with CloudKit

## Prerequisites

1. Edit your App ID Configuration to make the capabilities enabled: CloudKit(Add and enable container), Push Notifications.

## Add CloudKit Capabilities

1. Add CloudKit capabilities to your Xcode project.

![Add CloudKit capabilities](./images/capability-icloud.png)

2. Add Background Modes capability to your Xcode project.

![Add Background Modes capability](./images/add-background-modes.png)

3. Enable CloudKit and add container. The container should match your app's bundle identifier.

![Enable CloudKit and add container](./images/enable-cloudkit-and-add-container.png)

## Questions

1. Provisioning profile "YourAppName" doesn't support the iCloud.your.bundle.identifier iCloud Container.

![Provisioning profile error](./images/enable-icloud-container.png)