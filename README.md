# wsdl-import-maven-plugin

Download WSDLs, imported WSDLs and referenced schema files. Schema and imported WSDL locations are rewritten to reference the local files.

## Usage example:

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
    <executions>
        <execution>
            <phase>generate-sources</phase>
            <goals>
                <goal>wsdl-import</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

### Run with a maven profile:
```xml
<profile>
    <id>updateWSDL</id>
    <build>
        <plugins>
            <plugin>
                <groupId>com.github.abelmarkus</groupId>
                <artifactId>wsdl-import-maven-plugin</artifactId>
                <!-- see above for configurations -->
            </plugin>
        </plugins>
    </build>
</profile>
```

### Or run directly from console:
```bash
mvn wsdl-import:wsdl-import
```
# Requirements

JDK8+
