# 一、加载过程

## 1、读取mybatis-config.xml配置文件

1. Resources 通过类加载器简化加载资源；
2. ClassLoaderWrapper 一个类来包装对多个类加载器的访问，使它们作为一个类加载器工作；
3. ClassLoaderWrapper 包含多个类加载器，采用循环方法使用类加载器加载配置文件资源 InputStream returnValue = cl.getResourceAsStream(resource);

## 2、构建SqlSessionFactory（框架初始化）

1. SqlSessionFactoryBuilder build SqlSessionFactory；
2. 通过资源初始化XMLConfigBuilder；
3. 在XMLConfigBuilder 初始化过程中首先初始化new XPathParser(inputStream, true, props, new XMLMapperEntityResolver())；
4. XMLMapperEntityResolver 是MyBatis DTD的离线实体解析程序
5. XPathParser 用来解析资源节点数据
6. 解析配置文件信息，并设置对应数据

