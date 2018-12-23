# weblogic-shared-lib
In multiple projects we are using common resources or dependencies so every time we need to include all resources and dependencies in every project, so if we create **common shared lib** for all projects and deploy on Application server like *Weblogic* and in that way we can use shared lib for all.


# Steps:
1) Create simple maven project and include all common dependencies in pom.
2) Packaging should be war.
3) Create MANIFEST.MF in src/main/resources/
4) We have to set some properties in MANIFEST.MF
  *Manifest-Version: 1.0
  Specification-Title: weblogic-share-lib-1.0
  Specification-Version: 1.0
  Implementation-Title: weblogic-share-lib-1.0
  Implementation-Version: 1.0
  Implementation-Vendor: Az MaYo.
  Extension-Name: weblogic-share-lib*
5) In pom.xml file please update build part like:
	
	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-war-plugin</artifactId>				
				<configuration>
					<attachClasses>true</attachClasses>
				</configuration>
			</plugin>
		</plugins>
	</build>
	
5) Now just do mvn clean install

# Now some steps for client appliction (where we will include this shared lib).
1) In weblogic.xml file (if not created then please create) add bellow lines according to you
	
	<wls:library-ref>
        	<wls:library-name>weblogic-shared-lib-1.0</wls:library-name>
        	<wls:exact-match>false</wls:exact-match>
    	</wls:library-ref>  
	
2) Update pom.xml file and include this dependency with scope **provided** like:
	
	<dependency>
		<groupId>com.az</groupId>
		<artifactId>weblogic-shared-lib</artifactId>
		<version>1.0</version>
		<scope>provided</scope>
		<classifier>classes</classifier>
    	</dependency>

That's it.
Now all the dependencies and resources those are in weblogic-shared-lib folder containing will be available for all the project those will include this **shared lib** in weblogic.xml file.

Please make sure shared lib should be deployed as **weblogic shared lib** and status is active. then deploye your project.
