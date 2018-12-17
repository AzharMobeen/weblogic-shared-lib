# weblogic-shared-lib
In multiple projects we are using common dependencies so every time we need to include in ever project if we create common shared lib for all the project and deploy on Application server like Weblogic and in that way we can make it simple.


# Steps:
1) create simple maven project and include all common dependencies into his pom.
2) packaging should be war.
3) create MANIFEST.MF in src/main/resources/
4) Then put details of this shared lib for weblogic Application sever in MANIFEST.MF
  Manifest-Version: 1.0
  Specification-Title: weblogic-share-lib-1.0
  Specification-Version: 1.0
  Implementation-Title: weblogic-share-lib-1.0
  Implementation-Version: 1.0
  Implementation-Vendor: Az MaYo.
  Extension-Name: weblogic-share-lib
5) now just do mvn clean install

# Now some steps for client appliction where we will include this shared lib.
1) In weblogic.xml file (if not created then please create) add bellow lines according to you
    <wls:library-ref>
        <wls:library-name>weblogic-shared-lib-1.0</wls:library-name>
        <wls:exact-match>false</wls:exact-match>
    </wls:library-ref>  
2) Update pom.xml file and include this dependency as provided like:
    <dependency>
			<groupId>com.az</groupId>
			<artifactId>weblogic-shared-lib</artifactId>
			<version>1.0</version>
			<scope>provided</scope>
		</dependency>

That's it.

Please make sure shared lib should be deployed as weblogic shared lib and status is active. then deploye your project.
