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


