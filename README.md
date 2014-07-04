<h1>ABOUT</h1>
This project is prepared to serve as a sample application for Hazelcast, the leading open source in-memory data grid . Here, Hazelcast's use case is HTTP Session Replication. 
 
<h2>Prerequisites</h2>
You should have installed Apache Tomcat7 and Apache Maven 3.2.1 on your system. Download links are given below. Choose appropriate one for you.

`Apache Tomcat7` - http://tomcat.apache.org/download-70.cgi <br />
`Apache Maven 3.2.1` - http://maven.apache.org/download.cgi<br />
`Hazelcast 3.3-XX` - http://hazelcast.com/products/hazelcast-enterprise/ 

<h2>Configuration</h2>

1) Extract .zip file. Drop hazelcast-3.3-XX-ee.jar and hazelcast-sessions-tomcat7-3.3-XX.jar to your tomcat-installation-path/lib. They are under /lib of extracted folder of Hazelcast.<br />

2) You must put hazelcast.xml file to tomcat-installation-directory/lib . You can find a sample hazelcast.xml file under extracted-hazelcast-folder/bin. Additionally, in hazelcast.xml, put your license key between `<license-key>` and `</license-key>` tags. 

3) Open tomcat7-installation-folder/conf/context.xml file and add this line

`<Manager className="com.hazelcast.session.HazelcastSessionManager" sticky="true" clientOnly="false" />`
between `<Context>` and `</Context>` tags.

4) Open tomcat7-installation-folder/conf/server.xml file and add a listener

`<Listener className="com.hazelcast.session.P2PLifecycleListener"  configLocation="hazelcast.xml"/>`

5) You can change your preferences as `sticky="false"` or `clientOnly="true"`. But if you change your preferences as `clientyOnly="true"`, you must remove your listener from `server.xml` file
<br />

<h2>How to Run Sample Application</h2>

BEFORE-STARTING : Make sure tomcat-installation-path/startup.sh and tomcat-installation-path/shutdown.sh are executable. You can make them executable via `chmod +x startup.sh` and `chmod +x shutdown.sh` if your working directory is tomcat-installation-path. 

1) go to tomcat-installation-path/bin and run startup.sh shell file from terminal.

2) clone the repository via `git clone https://github.com/hazelcastInternsSummer14/sessionReplicationApp.git`

3) then go to sessionReplicationApp/example folder.

4) run maven via `mvn package`

5) maven creates example.war file under sessionReplicationApp/example/target folder.

6) copy example.war file to tomcat7-installation-path/webapps folder

7) open a browser and enter `localhost:8080/example/hazelcast`

Built with love in Istanbul.

<h2>NOTES</h2>
- You can use Apache Tomcat 6 instead of Tomcat 7.
- 
