
---
[current page link](https://github.com/littleostar-angular/maven-webapp-load-angular)

---

#### access right angular on tomcat

##### a: RouterModule.forRoot(routes, {useHash: true})

drawback: the website url have "#", disadvantage, google hard search it.


##### b: setting tomcat server

b.1 in Tomcat’s "/conf" directory, add "REWRITE VALVE" to "context.xml" file.

-Here’s an example of setting the valve in Tomcat’s context.xml

    <?xml version='1.0' encoding='utf-8'?>
    <!-- The contents of this file will be loaded for each web application -->
    <Context>
        <!-- REWRITE VALVE -->
        <Valve className="org.apache.catalina.valves.rewrite.RewriteValve" />
        <!-- // -->
  
        <!-- Speed up context loading -->
        <JarScanner scanClassPath="false" />
        <!-- Default set of monitored resources. If one of these changes, the -->
        <!-- web application will be reloaded.                                -->
        <WatchedResource>WEB-INF/web.xml</WatchedResource>
        <WatchedResource>${catalina.base}/conf/web.xml</WatchedResource>
    </Context>

b.2 use intellij idea create a maven-archetype-webapp (javaweb) project.

b.3 build angular get app(--baseHref=.), put angular app to javaweb project webapp floder.

b.4 create a file, name is "rewrite.config".

-put those code to "rewrite.config".

    RewriteCond %{REQUEST_URI} !^.*\.(bmp|css|gif|htc|html?|ico|jpe?g|js|pdf|png|swf|txt|xml|svg|eot|woff|woff2|ttf)$
    RewriteRule ^(.*)$ index.cfm/$1 [L]

b.5 put "rewrite.config" file on WEB-INF folder.

b.6 build maven-webapp project, get war file, put war to tomcat webapps folder. run it. success.

![Maven webapp project structure image](https://github.com/littleostar-angular/maven-webapp-load-angular/blob/master/_image/XtZpG.jpg?raw=true)

---

#### edit configuration run maven-angular on tomcat use intellij-idea

a. add tomcat server

b. deployment xxx.war

c. run tomcat configuration

---
end