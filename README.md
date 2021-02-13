# Wsdl Import Maven Plugin
[![Maven Central](https://img.shields.io/maven-central/v/com.github.abelmarkus/wsdl-import-maven-plugin.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22com.github.abelmarkus%22%20AND%20a:%22wsdl-import-maven-plugin%22)
![Maven Build](https://github.com/abelmarkus/wsdl-import-maven-plugin/workflows/Maven%20Build/badge.svg)
![CodeQL](https://github.com/abelmarkus/wsdl-import-maven-plugin/workflows/CodeQL/badge.svg)
[![License](https://img.shields.io/badge/License-Apache%20License%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

Download WSDLs, imported WSDLs and referenced schema files. Schema and imported WSDL locations are rewritten to reference the local files.

## Usage example:

```xml
<plugin>
    <groupId>com.github.abelmarkus</groupId>
    <artifactId>wsdl-import-maven-plugin</artifactId>
    <version>1.0.2</version>
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
