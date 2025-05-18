1. ****BeanFactory(I)**** – Available in org.springframework.beans.factory package.
2. ****ApplicationContext(I)**** – Available in org.springframework.context package.

### BeanFactory

This is the root interface for accessing a Spring bean container. It is the actual container that instantiates, configures, and manages a number of beans. 

These beans collaborate with one another and thus have dependencies between themselves. These dependencies are reflected in the configuration data used by the BeanFactory. 

This interface is implemented by the objects that hold a number of bean definitions, each uniquely identified by a String name. The most common implementation class used for this BeanFactory is ****XmlBeanFactory**** available in ****org.springframework.beans.factory.xml package.**** 

****Example code:****
```
ClassPathResource resource = new ClassPathResource("beans.xml");  
XmlBeanFactory factory = new XmlBeanFactory(resource);
```


### Bean Creation

Using BeanFactory, the beans will be initialized when the **getBean()** method is called, which means on-demand. But the ApplicationContext will initialize all the beans **at the startup only**.

### ApplicationContext Interface

This interface is designed on top of the BeanFactory interface. The ApplicationContext interface is the advanced container that enhances BeanFactory functionality in a more framework-oriented style. 

While the BeanFactory provides basic functionality for managing and manipulating beans, often in a programmatic way, the ApplicationContext provides extra functionality like MessageSource, Access to resources, Event propagation to beans, Loading of multiple (hierarchical) contexts etc. 

There are so many implementation classes that can be used such as ****ClassPathXmlApplicationContext****, ****FileSystemXmlApplicationContext****, ****AnnotationConfigWebApplicationContext**** etc.

****Example code:****
```
ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
```

### Interface Hierarchy

Below is the hierarchy of the BeanFactory(I) and ApplicationContext(I) with some of their implementation classes.

![Hierarchy Structure](https://media.geeksforgeeks.org/wp-content/uploads/20220221172216/Hi.jpg)

## Conclusion

**BeanFactory** is the fundamental interface that provides all the basic functionality to create and manage the bean objects and the **ApplicationContext** interface extends the BeanFactory interface, it provides all the basic functionality and also some advanced features like the ability to load file resources in a generic fashion, to publish events to registered listeners, to resolve messages, supporting internationalization, etc.