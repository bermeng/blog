# cordova签名app

* 生成keystore

```Bash
keytool -genkeypair -alias name.keystore -keyalg RSA -validity 4000 -keystore name.keystore
```

* 将build生成的unsigned的apk移动到和第一步生成的name.keystore同一文件夹下

* 进行签名

```Bash
jarsigner -verbose -keystore name.keystore -signedjar name.apk name_unsigned.apk name.keystore
```