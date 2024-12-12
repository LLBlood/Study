# 一、资源管理

## 1.1 JAVA url 资源管理

### 1.1.1 基础代码

```java
public class URLStudy {
    public static void main(String[] args) throws Exception {
        URL url = new URL("https://www.baidu.com");
        URLConnection urlConnection = url.openConnection();
        InputStream inputStream = urlConnection.getInputStream();
        byte[] bytes = new byte[1024];
        int size = 0;
        StringBuilder sb = new StringBuilder();
        while ((size = inputStream.read(bytes)) != -1) {
            sb.append(new String(bytes, 0, size));
        }
        System.out.println(sb.toString());
    }
}
```

1. 第一行将请求字符串转变为统一资源定位符URL，实例化的同时，设置https的URLStreamHandler实现，通过解析协议，并约定URLStreamHandler实现包放置目录，通过工厂模式+反射操作，将Handler注入进来；有个疑问为什么hanlders初始化有数据

## 1.2 Spring Resource 资源管理

