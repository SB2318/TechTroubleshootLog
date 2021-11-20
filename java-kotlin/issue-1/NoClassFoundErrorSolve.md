
Here we will be going to discuss an error, the exact explanation of which I have not yet found. But the purpose for me was to learn the thing where this error was prevented. Anyway, I have come up with a solution that works.
First, take a look at that problem.
 
# Problem:

---
  

Recently, I have faced this problem. I was learning Kotling programming. I am using IntelliJ for this purpose.
While reading about <a href="https://kotlinlang.org/docs/java-interop.html">**Interoperability**</a>, I came across the problem.
  
```
Exception in thread "main" java.lang.NoClassDefFoundError: MyJava
	at MyKotlinKt.main(MyKotlin.kt:5)
Caused by: java.lang.ClassNotFoundException: MyJava
	at java.net.URLClassLoader.findClass(URLClassLoader.java:382)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:418)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:355)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:351)
	... 1 more

Process finished with exit code 1

```
Here is my Java code.
```
public class MyJava {

	public static void main(String[] args){

	}

	public static int getArea(int length,int breadth){

		return length*breadth;
	}

	public int add(int a, int b){

		return (a+b);
	}
}

```
It may seem to you that there is a problem with my build.gradle.kts file.
Please go through this <a href="https://discuss.kotlinlang.org/t/noclassdeffound-with-kotlin-java-project/20458">link</a> also. My problem is similar to this.

# Solution:

---
![Screenshot (283)](https://user-images.githubusercontent.com/87614560/142712979-9f37c502-6256-4ce8-89e6-3e118160bc0d.png)
---
Initially, our project source folder looks like this.
The solution to this problem is that we need to create another directory named **java.**

![directory](https://user-images.githubusercontent.com/87614560/142713161-d3b303b0-075d-490b-a535-f9938440f080.png)


Then I run the application after pasting the `MyJava.java` file into the `java` directory.

![runapp](https://user-images.githubusercontent.com/87614560/142713233-736eb907-32b2-4458-86a9-129339de9a8a.png)

Although the application was running, there were still some errors in the `build.gradle.kts` file.

![builderror](https://user-images.githubusercontent.com/87614560/142713281-589984db-d70a-4c33-95ff-3ed8507e599d.png)
---
To get rid of this problem, We have to go to the build.gradle.kts file and set our source. Just paste the following code in any space inside that file.

```
sourceSets.main {
    java.srcDirs("src/main/myJava", "src/main/myKotlin")
}

```
In my case this error was removed.

![sourceset](https://user-images.githubusercontent.com/87614560/142713562-7b505bd3-1ee5-44c2-881f-046eda02b961.png)
---
## Reference:
---
* https://kotlinlang.org/docs/gradle.html#kotlin-and-java-sources
* https://maven.apache.org/guides/introduction/introduction-to-the-pom.html


Fixes <a href="https://github.com/SB2318/kotlin-java-project-error/issues/1">#1</a>




