# bookstore4010web
a simple Grails 4.0.10 web application created via the Grails Application Forge web site

Previously I used my MS Windows 10 Pro laptop (a Dell XPS 15) to visit the Grails Application Forge web site (http://start.grails.org/) and generated 
three Grails 4.0.10 web applications -- one for the "web" profile, one for the "angular" profile, and one for the "rest-api" profile.

```
https://start.grails.org/

Grails Application Forge

curl -O https://start.grails.org/bookstore4010web.zip -d version=4.0.10
curl -O https://start.grails.org/bookstore4010ang.zip -d version=4.0.10 -d profile=angular
curl -O https://start.grails.org/bookstore4010res.zip -d version=4.0.10 -d profile=rest-api

04/10/2021  10:23 AM           808,223 bookstore4010web.zip
04/10/2021  10:24 AM           265,096 bookstore4010ang.zip
04/10/2021  10:29 AM            92,201 bookstore4010res.zip
```

This github repository reflects my work with the "web" profile "bookstore4010web" Grails 4.0.10 web application.

Here are the files I downloaded in order to work on this project:

```
01/20/2021  08:10 AM       175,084,680 jdk-8u281-windows-x64.exe
01/20/2021  08:15 AM       180,005,376 jdk-11.0.10_windows-x64_bin.zip
03/18/2021  07:08 AM       544,526,125 eclipse-jee-2021-03-R-win32-x86_64.zip
03/18/2021  07:12 AM       343,797,569 eclipse-java-2021-03-R-win32-x86_64.zip
04/08/2021  06:17 PM       934,924,625 ideaIU-2021.1.win.zip
04/08/2021  06:20 PM       810,305,520 ideaIC-2021.1.win.zip
04/08/2021  06:21 PM        98,847,948 VSCode-win32-x64-1.55.1.zip
04/09/2021  07:28 AM       132,381,687 grails-4.0.10.zip
03/18/2021  06:56 AM       157,861,136 jdk-16_windows-x64_bin.exe
03/18/2021  06:57 AM       176,936,924 jdk-16_windows-x64_bin.zip
```

Afer installing the two versions of the Oracle Java JDK (8u281 and 11.0.10), Grails 4.0.10, and the JetBrains IntelliJ IDEA 2021.1, I used the command line to build 
the simple "bookstore4010web" web application and test it with the Firefox web browser (at URL http://localhost:8080).  For this initial work I used the Oracle Java 8u281 JDK.

```
Microsoft Windows [Version 10.0.19042.906]
(c) Microsoft Corporation. All rights reserved.

C:\Users\David Holberton>grails --version
| Grails Version: 4.0.10
| JVM Version: 1.8.0_281
C:\Users\David Holberton>java -version
java version "1.8.0_281"
Java(TM) SE Runtime Environment (build 1.8.0_281-b09)
Java HotSpot(TM) 64-Bit Server VM (build 25.281-b09, mixed mode)

C:\Users\David Holberton>
```

Here is the command line activity for the initial build of the "bookstore4010web" Grails 4.0.10 web application:

```
cd "\Users\David Holberton"
mkdir g2mprojects
cd Downloads
copy bookstore4010web.zip ..\g2mprojects
cd ..\g2mprojects
7z l bookstore4010web.zip > ..\bookstore4010web.zip.txt
7z x bookstore4010web.zip
cd bookstore4010web
tree /a    > ..\..\bookstore4010web-tree-a.txt
tree /a /f > ..\..\bookstore4010web-tree-af.txt
git init
git add .
git commit -a -m "initial commit"
git remote add origin git@github.com:ashburndev/bookstore4010web.git
git branch -M main
git push -u origin main
grails run-app
grails create-domain-class Book
notepad grails-app\domain\bookstore4010web\Book.groovy
grails generate-all bookstore4010web.Book
grails schema-export
copy .\build\ddl.sql ..\..\bookstore4010web.ddl.sql
grails dependency-report > ..\..\bookstore4010web.dependency.report
grails run-app

git fetch
git pull
git status
copy ..\..\bookstore4010web* .
git add .
git commit -a -m "add Book domain class, other documentation artifacts"
git push
```
```
C:\Users\David Holberton\g2mprojects\bookstore4010web>date /t
Sat 04/10/2021

C:\Users\David Holberton\g2mprojects\bookstore4010web>git log --pretty=format:"%h - %an, %ai : %s"
b41c163 - ashburndev, 2021-04-10 18:05:39 -0400 : add Book domain class, other documentation artifacts
460e66e - ashburndev, 2021-04-10 17:24:49 -0400 : initial commit

C:\Users\David Holberton\g2mprojects\bookstore4010web>
```

After everything worked without any problems using the Oracle Java 8u281 JDK, I switched to the Oracle Java 11.0.10 JDK and tried building and running the applicaiton again. 
Despite all the grails warnings I received below, everything appears to be working correctly.

```
C:\Users\David Holberton>echo %JAVA_HOME%
C:\LocalApps\Java\jdk1.8.0_281

C:\Users\David Holberton>echo %JAVA_HOME%
C:\LocalApps\Java\jdk-11.0.10

C:\Users\David Holberton>java -version
java version "11.0.10" 2021-01-19 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.10+8-LTS-162)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.10+8-LTS-162, mixed mode)

C:\Users\David Holberton>
C:\Users\David Holberton>cd g2mprojects\bookstore4010web
C:\Users\David Holberton\g2mprojects\bookstore4010web>
C:\Users\David Holberton\g2mprojects\bookstore4010web>grails --version
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.reflection.CachedClass (file:/C:/LocalApps/grails-4.0.10/lib/org.codehaus.groovy/groovy/jars/groovy-2.5.14.jar) to method java.lang.Object.finalize()
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.reflection.CachedClass
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
| Grails Version: 4.0.10
| JVM Version: 11.0.10
C:\Users\David Holberton\g2mprojects\bookstore4010web>grails clean
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.reflection.CachedClass (file:/C:/LocalApps/grails-4.0.10/lib/org.codehaus.groovy/groovy/jars/groovy-2.5.14.jar) to method java.lang.Object.finalize()
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.reflection.CachedClass
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
| Resolving Dependencies. Please wait...

CONFIGURE SUCCESSFUL in 3s

BUILD SUCCESSFUL in 1s
1 actionable task: 1 executed
C:\Users\David Holberton\g2mprojects\bookstore4010web>grails run-app
C:\Users\David Holberton\g2mprojects\bookstore4010web>grails run-app
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.reflection.CachedClass (file:/C:/LocalApps/grails-4.0.10/lib/org.codehaus.groovy/groovy/jars/groovy-2.5.14.jar) to method java.lang.Object.finalize()
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.reflection.CachedClass
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
| Running application...
The Class-Path manifest attribute in C:\Users\David Holberton\.gradle\caches\modules-2\files-2.1\org.glassfish.jaxb\jaxb-runtime\2.3.1\dd6dda9da676a54c5b36ca2806ff95ee017d8738\jaxb-runtime-2.3.1.jar referenced one or more files that do not exist: file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/org.glassfish.jaxb/jaxb-runtime/2.3.1/dd6dda9da676a54c5b36ca2806ff95ee017d8738/jaxb-api-2.3.1.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/org.glassfish.jaxb/jaxb-runtime/2.3.1/dd6dda9da676a54c5b36ca2806ff95ee017d8738/txw2-2.3.1.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/org.glassfish.jaxb/jaxb-runtime/2.3.1/dd6dda9da676a54c5b36ca2806ff95ee017d8738/istack-commons-runtime-3.0.7.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/org.glassfish.jaxb/jaxb-runtime/2.3.1/dd6dda9da676a54c5b36ca2806ff95ee017d8738/stax-ex-1.8.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/org.glassfish.jaxb/jaxb-runtime/2.3.1/dd6dda9da676a54c5b36ca2806ff95ee017d8738/FastInfoset-1.2.15.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/org.glassfish.jaxb/jaxb-runtime/2.3.1/dd6dda9da676a54c5b36ca2806ff95ee017d8738/javax.activation-api-1.2.0.jar
The Class-Path manifest attribute in C:\Users\David Holberton\.gradle\caches\modules-2\files-2.1\com.sun.xml.bind\jaxb-impl\2.3.1\a1a12b85ba1435b4189e065f7dafcc3fb9410d38\jaxb-impl-2.3.1.jar referenced one or more files that do not exist: file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/com.sun.xml.bind/jaxb-impl/2.3.1/a1a12b85ba1435b4189e065f7dafcc3fb9410d38/jaxb-runtime-2.3.1.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/com.sun.xml.bind/jaxb-impl/2.3.1/a1a12b85ba1435b4189e065f7dafcc3fb9410d38/txw2-2.3.1.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/com.sun.xml.bind/jaxb-impl/2.3.1/a1a12b85ba1435b4189e065f7dafcc3fb9410d38/istack-commons-runtime-3.0.7.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/com.sun.xml.bind/jaxb-impl/2.3.1/a1a12b85ba1435b4189e065f7dafcc3fb9410d38/stax-ex-1.8.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/com.sun.xml.bind/jaxb-impl/2.3.1/a1a12b85ba1435b4189e065f7dafcc3fb9410d38/FastInfoset-1.2.15.jar,file:/C:/Users/David%20Holberton/.gradle/caches/modules-2/files-2.1/com.sun.xml.bind/jaxb-impl/2.3.1/a1a12b85ba1435b4189e065f7dafcc3fb9410d38/javax.activation-api-1.2.0.jar
<==========---> 83% EXECUTING [8s]
> :bootRun
```
