This repository is intended to contain only external jars, which are required in EaaS projects. Every branch here is an external library, which could be added to your project via link:

https://raw.githubusercontent.com/eaas-framework/external-libraries/BRANCH_NAME

In order to create a maven repo from jar, you could use this command:
```
mvn install:install-file -Dfile=<path-to-file>  -DgroupId=<group-id> 
-DartifactId=<artifact-id>  -Dversion=<version>  -Dpackaging=<packaging>
```
OR
put following plugin to your pom and then run `mvn install`. It will create a repo in *~/.m2/repository/* directory. Then you can copy created directory to git (as a separate branch).
```
<plugin>  
   <groupId>org.apache.maven.plugins</groupId>  
   <artifactId>maven-install-plugin</artifactId>  
   <version>2.5.1</version>  
   <executions>  
      <execution>  
         <id>install-handle-client</id>  
         <phase>validate</phase>  
         <goals>  
            <goal>install-file</goal>  
         </goals>  
         <configuration>  
            <file>FILE_PATH</file>  
            <groupId>GROUP_ID</groupId>  
            <artifactId>ARTIFACT_ID</artifactId>  
            <version>VERSION</version>  
            <packaging>jar</packaging>  
            <createChecksum>true</createChecksum>  
            <generatePom>true</generatePom>  
         </configuration>  
      </execution>  
   </executions>  
</plugin>
```
