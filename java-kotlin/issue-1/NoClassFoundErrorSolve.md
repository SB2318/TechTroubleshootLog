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
![](images/initial.png)

