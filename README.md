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

![autoconfig](https://user-images.githubusercontent.com/54987617/203244627-f9a35043-c152-4ec2-9d37-7bfdbd83b50b.png)

In the picture we clearly see that there is a condition on datasource.class that means jpa repository will be enabled only when datasource bean is present in the class path.
