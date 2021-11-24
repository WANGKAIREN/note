# List对象取单个字段

```java
List<String> iccidList = cardList.stream().map(Card::getIccid).collect(Collectors.toList());
```

[参考](https://blog.csdn.net/weixin_42315706/article/details/113025343)