# 遭遇到 Log not mocked

java.lang.RuntimeException: Method d in android.util.Log not mocked. See http://g.co/androidstudio/not-mocked for details.

# 解法

```
android {
  // ...
  testOptions { 
    unitTests.returnDefaultValues = true
  }
}
```
