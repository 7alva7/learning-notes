# Notes

## 1. How do I check where my app is using IDFA?

```bash
grep -lr "advertisingIdentifier" * | grep -v .svn | grep -v .md
```

or 

```bash
grep -r advertisingIdentifier .
```