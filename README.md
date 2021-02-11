# wsdlget-maven-plugin

Download WSDLs, imported WSDLs and referenced schema files. Schema and imported WSDL locations are rewritten to reference the local files.

Usage example:

```xml
<plugin>
    <groupId>com.github.abelmarkus</groupId>
    <artifactId>wsdl-import-maven-plugin</artifactId>
    <version>1.0.1</version>
    <configuration>
        <clearOutputDirectory>true</clearOutputDirectory>
        <outputPath>path/to/desired/output</outputPath>
        <subfolderByServiceName>false</subfolderByServiceName>
        <wsdls>
          <wsdl>
            <url>http://someurl/service.wsdl</url>
          </wsdl>
          <wsdl>
            <serviceName>betterNameForDownloadedFiles</serviceName>
            <url>http://someurl/anotherService.wsdl</url>
          </wsdl>
        </wsdls>
    </configuration>
</plugin>
```

*mvn wsdlget:wsdlget*

# Requirements

Right now, at least Java Version 8
