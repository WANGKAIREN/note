# uniapp打包的app使用微信app支付，只有第一次能拉起支付，之后再也拉不起来支付

只有第一次能拉起支付，之后再也拉不起来支付，报错 -1，是被微信拉黑了，在微信软件本地拉黑此商户，卸载微信则拉黑信息被删除，可再次测试

**uniapp打包**：没有xxxx.keystore证书，不能测试
**android studio打包**：会生成一个临时的签名（xxxx.keystore），但是用来测试微信支付，不能用

**需要正式的android打包**：
1. 申请一个xxxx.keystore证书
2. 打包时需要证书，需要设置包名（与微信支付配置应用中的包名一致）
3. 用手机App `签名检查工具`上输入包名，得到格式化后的xxxx.keystore中的MD5签名，去冒号，变小写
4. 将格式化后的签名设置到微信支付的应用配置上

**xxxx.keystore证书**：
1. 其中包含各种加密格式的签名，比如MD5
2. 查看xxxx.keystore中的内容，需要Java运行环境，使用`keytool`工具
    `keytool -list  -v -keystore xxxx.keystore -storepass 证书密码`

[uniapp打包的app使用微信app支付，只有第一次能拉起支付，之后再也拉不起来支付 | 微信开放社区](https://developers.weixin.qq.com/community/pay/doc/000ac0418bc188d2038c0ddbf56800)