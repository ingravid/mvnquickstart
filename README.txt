# mvnquickstart
Maven basic Java project from its quickstart archetype 


* This project maven archetype command:

mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DoutputDirectory=./ -DgroupId=kos.mydemo -DartifactId=theDemo -Dpackage=myPackage -Dversion=0.1 

  * Custom properties
    -DoutputDirectory=./ #The relative path from the current, wheere it shall be installed.
    -DgroupId=kos.mydemo #Your project groupId com.mycompany, org.myorg, etc
    -DartifactId=theDemo #Your app name usually
    -Dpackage=myPackage #This parameter will define the package where the class with the java main method will be placed (!!!)
  
* The pom.xml file must be updated from the Maven original:

  - Replace:
  
        <plugin>
          <artifactId>maven-jar-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>

  - By:
  	<plugin>
        	<groupId>org.apache.maven.plugins</groupId>
		<artifactId>maven-jar-plugin</artifactId>
			<configuration>
				<archive>
					<manifest>
						<mainClass>
							[ THE Dpackage YOU'D SPECIFIED].App
						</mainClass>
					</manifest>
				</archive>
			</configuration>
	</plugin>
	
* May be you want to change the original version. In the pom.xml, just here:

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.7</maven.compiler.source>
    <maven.compiler.target>1.7</maven.compiler.target>
  </properties>

        
* Ready to run:

mvn clean install

* Run it 

java -jar target/theDemo-0.1.jar
