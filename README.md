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

## Details
The configuration takes following parameters:
1. clearOutputDirectory: if true delete output directory and all its content.
2. outputPath: the target directory to write all downloaded files to  (default: src/main/resources/wsdl).
3. subfolderByServiceName: if true add a subfolder to target directory based on serviceName stated in `wsdl` section.
4. `wsdl` url: the URL of the WSDL file
5. `wsdl` serviceName: better name for downloaded files

### clearOutputDirectory
if you want your target directory to be cleared at the beginning of the process.

### outputPath
The output folder to write all files to.

### subfolderByServiceName
Add a subfolder to target directory based on serviceName declared in `wsdl` section.

### `wsdl` url
This parameter references the URL location of the WSDL file to download.

As of current version of this plugin, no proxy servers are supported, so the WSDL must be reachable directly. Also, the location must not be protected (e.g. no basic auth).

### `wsdl` serviceName
The base name for the output files.

Taking 'someservice' as example serviceName, this files will be written, assuming that the WSDL file contains two schema imports:
* someservice.wsdl
* someservice0.xsd
* someservice1.xsd

The schema files will be named with a counting number, beginning at 0. The original schema file name from the WSDL file will be ignored and replaced by this name.

## Run with a maven profile:
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
