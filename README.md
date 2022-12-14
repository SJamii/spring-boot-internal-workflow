# spring-boot-internal-workflow

First of all we add spring-starter-web, spring-starter-test and so on in the build path in pom.xml file.
what they do is installing the jar file. Once this jar file are in our build path, there
are some files in the jar name as spring.factories. Folder structure is -

* META-INF/spring.factories

Inside the spring.factories file, spring developers mentioned what should be disable and what should be enable in the runtime based on some condition.
There should be anotation called @conditional (spring v4 @profiler in previous version) and @configuration to enable and disable the functionality of a specific jar file.

Go to -
* External Libraries/spring-boot-autoconfigure/META-INF/spring.factories to find the file.

If we use jpa repository as an example then we have to search for jparepository inside the spring.factories file. And then navigate that class name as JpaRepositoriesAutoConfiguration. Inside the file we can see something like this:

![autoconfig](https://user-images.githubusercontent.com/54987617/203246144-98bfbc08-dbe3-476c-81fd-2137ad257277.jpg)


In the picture we clearly see that there is a condition on datasource.class that means jpa repository will be enabled only when datasource bean is available in the class path. And also when jparepository related class present and other condition is satisfied then it will enable the jpa repository component.
Whatever we add in pox.xml, all the component related to those jar will  be available in the spring.factories file.
Which component will be enabled or disabled are maintained by some conditions. These condition will be found in following pictures.

![springBoot2](https://user-images.githubusercontent.com/54987617/203488915-230ebed1-09a2-49d6-a861-742d55ad8002.png)
