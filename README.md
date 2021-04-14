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

Using Eclipse 2021-03 as an IDE to develop this Grails 4.0.10 web application

I installed (unzipped) the Eclipse 2021-03 zip file into directory C:\LocalApps\eclipse-jee-2021-03-R-win32-x86_64

Then I following the instructions on web page https://github.com/groovy/groovy-eclipse/wiki to install the corresponding groovy-eclipse plugin

```
Once you have a compatible Eclipse installed, then ... follow these steps:

Note: I used the 4.19 (2021-03) https://dist.springsource.org/release/GRECLIPSE/e4.19 update site.

    Go to Help > Install New Software...
    Click on Add...
    Paste the update site URL appropriate for your version of Eclipse and click Add
    Select the new entry in the Work with list of update sites
    Expand Main Package and select the Eclipse Groovy Development Tools feature
    Click Next and follow the remaining prompts
```

Here is a list of the available groovy-eclipse update sites.

```
Eclipse Level 	Release Update Site
4.19 (2021-03) 	https://dist.springsource.org/release/GRECLIPSE/e4.19
4.18 (2020-12) 	https://dist.springsource.org/release/GRECLIPSE/e4.18
4.17 (2020-09) 	https://dist.springsource.org/release/GRECLIPSE/e4.17
4.16 (2020-06) 	https://dist.springsource.org/release/GRECLIPSE/e4.16
4.15 (2020-03) 	https://dist.springsource.org/release/GRECLIPSE/e4.15
4.14 (2019-12) 	https://dist.springsource.org/release/GRECLIPSE/e4.14
4.13 (2019-09) 	https://dist.springsource.org/release/GRECLIPSE/e4.13
4.12 (2019-06) 	https://dist.springsource.org/release/GRECLIPSE/e4.12
4.11 (2019-03) 	https://dist.springsource.org/release/GRECLIPSE/e4.11
4.10 (2018-12) 	https://dist.springsource.org/release/GRECLIPSE/e4.10
4.9 (2018-09) 	https://dist.springsource.org/release/GRECLIPSE/e4.9
4.8 (Photon) 	https://dist.springsource.org/release/GRECLIPSE/e4.8
4.7 (Oxygen) 	https://dist.springsource.org/release/GRECLIPSE/e4.7
4.6 (Neon) 	https://dist.springsource.org/release/GRECLIPSE/e4.6
4.5 (Mars) 	https://dist.springsource.org/release/GRECLIPSE/e4.5
4.4 (Luna) 	https://dist.springsource.org/release/GRECLIPSE/e4.4
4.3j8 (Kepler with Java 8 patch) 	https://dist.springsource.org/release/GRECLIPSE/e4.3-j8
4.3 (Kepler) 	https://dist.springsource.org/release/GRECLIPSE/e4.3
```

Here is the tail end of a directory listing of the plugins directory after performing the steps above.

```
03/12/2021  07:11 AM           301,183 org.jacoco.agent_0.8.6.v20201001-1506.jar
03/12/2021  07:11 AM           231,091 org.jacoco.core_0.8.6.v20201001-1506.jar
03/12/2021  07:11 AM           149,420 org.jacoco.report_0.8.6.v20201001-1506.jar
03/12/2021  07:11 AM         1,687,125 org.jcodings_1.0.18.v20170306-1742.jar
03/12/2021  07:11 AM           182,664 org.jdom_1.1.1.v201101151400.jar
03/12/2021  07:11 AM           214,637 org.joni_2.1.11.v20170306-1742.jar
03/12/2021  07:11 AM           344,634 org.jsoup_1.8.3.v20181012-1713.jar
03/12/2021  07:11 AM           204,027 org.junit.jupiter.api_5.7.1.v20210222-1948.jar
03/12/2021  07:11 AM           236,860 org.junit.jupiter.engine_5.7.1.v20210222-1948.jar
03/12/2021  07:11 AM            44,407 org.junit.jupiter.migrationsupport_5.7.1.v20210222-1948.jar
03/12/2021  07:11 AM           606,326 org.junit.jupiter.params_5.7.1.v20210222-1948.jar
03/12/2021  07:11 AM           118,078 org.junit.platform.commons_1.7.1.v20210222-1948.jar
03/12/2021  07:11 AM           206,807 org.junit.platform.engine_1.7.1.v20210222-1948.jar
03/12/2021  07:11 AM           159,700 org.junit.platform.launcher_1.7.1.v20210222-1948.jar
03/12/2021  07:11 AM            34,292 org.junit.platform.runner_1.7.1.v20210222-1948.jar
03/12/2021  07:11 AM            31,163 org.junit.platform.suite.api_1.7.1.v20210222-1948.jar
03/12/2021  07:11 AM            82,642 org.junit.vintage.engine_5.7.1.v20210222-1948.jar
03/12/2021  07:11 AM           425,413 org.junit_4.13.0.v20200204-1500.jar
03/12/2021  07:11 AM            83,522 org.objectweb.asm.commons_8.0.1.v20200420-1007.jar
03/12/2021  07:11 AM            66,018 org.objectweb.asm.tree_8.0.1.v20200420-1007.jar
04/14/2021  07:20 AM         7,288,622 org.eclipse.jdt.core_3.25.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM            16,989 org.codehaus.groovy.eclipse_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM            11,632 org.codehaus.groovy.eclipse.ant_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM            54,570 org.codehaus.groovy.eclipse.astviews_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM           289,170 org.codehaus.groovy.eclipse.codeassist_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM            92,594 org.codehaus.groovy.eclipse.codebrowsing_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM            20,957 org.codehaus.groovy.eclipse.compilerResolver_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM            82,773 org.codehaus.groovy.eclipse.core_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM           406,036 org.codehaus.groovy.eclipse.dsl_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM           117,621 org.codehaus.groovy.eclipse.quickfix_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM           283,958 org.codehaus.groovy.eclipse.refactoring_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM           562,768 org.codehaus.groovy.eclipse.ui_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM            18,935 org.codehaus.groovy.m2eclipse_4.1.0.v202103311613-e2103-RELEASE.jar
04/14/2021  07:20 AM           496,475 org.eclipse.jdt.groovy.core_4.1.0.v202103311613-e2103-RELEASE.jar
             925 File(s)    401,969,307 bytes
              27 Dir(s)  39,506,591,744 bytes free

C:\LocalApps\eclipse-jee-2021-03-R-win32-x86_64\plugins>
```
