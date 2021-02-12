# Wsdl Import Maven Plugin
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.github.abelmarkus/wsdl-import-maven-plugin/badge.svg?subject=Maven%20Central)](https://maven-badges.herokuapp.com/maven-central/com.github.abelmarkus/wsdl-import-maven-plugin/)
[![License](https://img.shields.io/badge/License-Apache%20License%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

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
`mvn wsdl-import:wsdl-import`