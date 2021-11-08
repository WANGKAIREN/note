# 错误: 编码 gbk 的不可映射字符 (0x80)

[草稿]

win11在`javac`时报错，编译失败，因为中文原因

使用记事本保存为ANSI编码可执行，但是使用如何使用Sublime Text修改为ANSI或可执行的编码呢？或者`javac`时如何指定编码呢？

```java
package test;

import utils.HttpsUtils;
import utils.Md5Utils;

import java.net.URLEncoder;
import java.util.ArrayList;
import java.util.List;
import java.util.Random;

/**
 * @author hezhuojian
 * @version 1.0
 * @date 2021/8/18 11:39
 */

public class Test {

    public static void main(String[] args) {

        sendSms();
    }

    private static void sendSms(){
        Random random = new Random();

        String userName = "1114";
        String password = "test123456";

        for (int i = 0; i < 100; i++) {
            String content = random.nextLong() + "【祝福】";
            String mobile = "18219112004";
            String url = "http://218.17.211.145:9001/smsSend" +
                    ".do?username=" + userName + "&password=" + Md5Utils.MD5Encode(userName + Md5Utils.MD5Encode(password)) +
                    "&content=" + content + "&mobile=" + mobile;
            System.out.println(HttpsUtils.get(url));
        }
    }
}
```


the encoding you've chosen('GBK') may change the contents of 'AutoUpdateCertificatesVerifier.java'.
Do you want to
1. Reload the file from disk in the new encoding 'GBK' and overwrite editor contents or
2. Convert the text and overwrite file in the new encoding?

[IDEA MSG](img/错误%20编码%20gbk%20的不可映射字符%20(0x80)-001.png)

选择Reload

Incompatible Encoding: GBK
File '*.java' most likely isn't stored in the 'GBK' encoding.

Why: charset is auto-detected from content
Current encoding: 'UTF-8'
[IDEA MSG](img/错误%20编码%20gbk%20的不可映射字符%20(0x80)-002.png)


cmd中
`javac *.java -encoding utf-8` 不会报错


## IDEA中解决方案

将Help—>Edit Cusuom VM Options...中添加`-Dfile.encoding=UTF-8`后不生效的话，删除`build`文件再重启

防止方案一未生效，可用方案二
在IDEA的安装目录下找到idea.exe.vmoptions和idea64.exe.vmoptions文件添加`-Dfile.encoding=UTF-8`

Settings->Editor->File Encodings全部改为UTF-8

更改文件的编码格式

Settings->Build，Ex***->Compiler-> 在Java Compiler中添加参数:-encoding utf-8

选择适合本工程的JDK版本

找到Maven的配置 取消委托给Maven的build/run的权利。

[IDEA编译的时候乱码](img/错误%20编码%20gbk%20的不可映射字符%20(0x80)-003.png)

[参考](https://www.jb51.net/article/215426.htm)