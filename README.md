# bookstore4010web
a simple Grails 4.0.10 web application created via the Grails Application Forge web site

Previously I used my MS Windows 10 Pro laptop (a Dell XPS 15) to visit the Grails Application Forge web site (http://start.grails.org/) and generated 
three Grails 4.0.10 web applications -- one for the "web" profile, one for the "angular" profile, and one for the "angular" profile.

```
11/14/2020  02:16 PM           807,978 bookstore405web.zip
11/14/2020  02:17 PM           264,485 bookstore405ng.zip
```

This github repository reflects my work with the "web" profile "bookstore405web" Grails 4.0.5 web application.

Here are the files I downloaded in order to work on this project:

```
07/16/2020  09:10 AM       174,353,032 jdk-8u261-windows-x64.exe
10/24/2020  09:13 AM       159,488,664 jdk-11.0.9_windows-x64_bin.exe
10/24/2020  09:14 AM       179,769,466 jdk-11.0.9_windows-x64_bin.zip
10/26/2020  06:14 AM       134,272,314 grails-4.0.5.zip
10/26/2020  06:14 AM         9,113,697 grails-docs-4.0.5.zip
11/14/2020  01:50 PM       697,317,424 ideaIU-2020.2.3.exe
11/14/2020  01:52 PM       806,810,701 ideaIU-2020.2.3.win.zip
11/14/2020  01:52 PM       601,519,616 ideaIC-2020.2.3.exe
11/14/2020  01:53 PM       675,182,337 ideaIC-2020.2.3.win.zip
```

Afer installing the two versions of the Oracle Java JDK (8u261 and 11.0.9), Grails 4.0.5, and the JetBrains IntelliJ IDEA, I used the command line to build 
the simple "bookstore405web" web application and test it with the Firefox web browser (at URL http://localhost:8080).  For this initial work I used the Oracle Java 8u261 JDK.

```
Microsoft Windows [Version 10.0.19042.630]
(c) 2020 Microsoft Corporation. All rights reserved.

C:\Users\David Holberton>grails --version
| Grails Version: 4.0.5
| JVM Version: 1.8.0_261
C:\Users\David Holberton>java -version
java version "1.8.0_261"
Java(TM) SE Runtime Environment (build 1.8.0_261-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.261-b12, mixed mode)

C:\Users\David Holberton>
```

Here is the command line activity for the initial build of the "bookstore405web" Grails 4.0.5 web application:

```
cd "\Users\David Holberton"
mkdir g2mprojects
cd Downloads
copy bookstore405web.zip ..\g2mprojects
cd ..\g2mprojects
7z l bookstore405web.zip > ..\bookstore405web.zip.txt
7z x bookstore405web.zip
cd bookstore405web
tree /a    > ..\..\bookstore405web-tree-a.txt
tree /a /f > ..\..\bookstore405web-tree-af.txt
git init
git add .
git commit -a -m "initial commit"
git remote add origin https://github.com/ashburndev/bookstore405web.git
git branch -M main
git push -u origin main
grails run-app

grails create-domain-class Book
notepad grails-app\domain\bookstore405web\Book.groovy
grails generate-all bookstore405web.Book
grails schema-export
copy .\build\ddl.sql ..\..\bookstore405web.ddl.sql
grails dependency-report > ..\..\bookstore405web.dependency.report
grails run-app

git fetch
git pull
git status
git add .
commit -a -m "add Book domain class, other documentation artifacts"
git push

git fetch
git pull
git status
git add .
commit -a -m "add bookstore405web.dependency.report text file"
git push
```
```
C:\Users\David Holberton\g2mprojects\bookstore405web>date /t
Wed 02/03/2021

C:\Users\David Holberton\g2mprojects\bookstore405web>git log --pretty=format:"%h - %an, %ai : %s"
486d08c - ashburndev, 2020-11-25 08:32:24 -0500 : add bookstore405web.dependency.report text file
d9fc41b - ashburndev, 2020-11-25 08:30:47 -0500 : Update README.md
5eeb24c - ashburndev, 2020-11-25 08:20:27 -0500 : deleted bookstore405-tree-af.txt
d5205e5 - ashburndev, 2020-11-25 08:17:12 -0500 : Update README.md
e31965b - ashburndev, 2020-11-25 08:14:27 -0500 : Merge branch 'main' of https://github.com/ashburndev/bookstore405web into main
51cd390 - ashburndev, 2020-11-25 08:13:20 -0500 : add Book domain class, other documentation artifacts
7cb6df9 - ashburndev, 2020-11-25 08:09:15 -0500 : Update README.md
7c17113 - ashburndev, 2020-11-25 07:41:23 -0500 : Create README.md
8a211b3 - ashburndev, 2020-11-25 06:26:03 -0500 : initial commit

C:\Users\David Holberton\g2mprojects\bookstore405web>
```

After everything worked without any problems using the Oracle Java 8u261 JDK, I switched to the Oracle Java 11.0.9 JDK and tried building and running the applicaiton again. 
Despite all the grails warnings I received below, everything appears to be working correctly.

```
C:\Users\David Holberton>echo %JAVA_HOME%
C:\LocalApps\Java\jdk1.8.0_261

C:\Users\David Holberton>
C:\Users\David Holberton>echo %JAVA_HOME%
C:\Program Files\Java\jdk-11.0.8

C:\Users\David Holberton>
C:\Users\David Holberton>echo %JAVA_HOME%
C:\LocalApps\Java\jdk-11.0.9

C:\Users\David Holberton>
C:\Users\David Holberton>java -version
java version "11.0.9" 2020-10-20 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.9+7-LTS)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.9+7-LTS, mixed mode)

C:\Users\David Holberton>grails --version
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.vmplugin.v7.Java7$1 (file:/C:/LocalApps/grails-4.0.5/lib/org.codehaus.groovy/groovy/jars/groovy-2.5.6.jar) to constructor java.lang.invoke.MethodHandles$Lookup(java.lang.Class,int)
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.vmplugin.v7.Java7$1
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
| Grails Version: 4.0.5
| JVM Version: 11.0.9
C:\Users\David Holberton>
C:\Users\David Holberton\g2mprojects\bookstore405web>grails clean
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.vmplugin.v7.Java7$1 (file:/C:/LocalApps/grails-4.0.5/lib/org.codehaus.groovy/groovy/jars/groovy-2.5.6.jar) to constructor java.lang.invoke.MethodHandles$Lookup(java.lang.Class,int)
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.vmplugin.v7.Java7$1
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
| Resolving Dependencies. Please wait...

CONFIGURE SUCCESSFUL in 3s

BUILD SUCCESSFUL in 1s
1 actionable task: 1 executed
C:\Users\David Holberton\g2mprojects\bookstore405web>grails run-app
```
