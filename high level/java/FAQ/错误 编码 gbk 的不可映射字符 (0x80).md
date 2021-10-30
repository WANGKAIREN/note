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