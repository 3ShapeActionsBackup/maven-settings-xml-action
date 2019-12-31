# maven-settings-xml-action

Github Action to update maven ~/.m2/settings.xml

[![CodeFactor](https://www.codefactor.io/repository/github/whelk-io/maven-settings-xml-action/badge)](https://www.codefactor.io/repository/github/whelk-io/maven-settings-xml-action)

## Inputs

### `servers`

**Optional** json array of servers to add to settings.xml.

### `repositories`
**Optional** json array of repositories to add to settings.xml

## Example usage

````yaml
- name: maven-settings-xml-action
  uses: whelk-io/maven-settings-xml-action@v2
  with:
    repositories: '[{ "id": "some-repository", "url": "http://some.repository.url" }]'
    servers: '[{ "id": "some-server", "username": "some.user", "password": "some.password" }]'
````

## Example `settings.xml`

````xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" 
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                              http://maven.apache.org/xsd/settings-1.0.0.xsd">
  
    <activeProfiles>
        <activeProfile>github</activeProfile>
    </activeProfiles>
  
    <profiles>
        <profile>
            <id>github</id>
            <repositories>
                <repository>
                    <id>central</id>
                    <url>https://repo1.maven.org/maven2</url>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                </repository>
                <repository>
                    <id>foo</id>
                    <url>http://foo.bar</url>
                </repository>
            </repositories>
        </profile>
    </profiles>
  
    <servers>
        <server>
            <id>foo</id>
            <username>fu</username>
            <password>bar</password>
        </server>
    </servers>
  
</settings>

````
