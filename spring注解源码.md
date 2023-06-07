# 一.IOC容器

## 1.xml配置 

```xml
<!-- 包扫描-->  
<context:component-scan base-package="com.yql"/>
<!--注册组件 -->
    <bean id="person" class="com.yql.bean.Person">
        <property name="name" value="张三"/>
        <property name="age" value="18"/>
    </bean>
```

### 1.2获取 bean对象

```java
        ApplicationContext applicationContext = new ClassPathXmlApplicationContext("beans.xml");
        Person person = (Person) applicationContext.getBean("person");
        System.out.println(person);
```



## 2.注解配置

### 	2.1 AnnotationConfigApplicationContext 

```java
AnnotationConfigApplicationContext applicationContext = new AnnotationConfigApplicationContext(类配置.class);

```

### 2.2 @Component

​	指示带注释的类是“组件”。当使用基于注解的配置和类路径扫描时，这些类被认为是自动检测的候选者。

2.3 
