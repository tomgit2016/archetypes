## A maven archetype for creating a single JAR packaged application

### Why create one

I had no luck finding a simple archetype to create a java application that can run by command `java -jar [jar_file_name]`, so I created this one. It includes `gson 2.8.2` and `apache commons-lang3` libraries. A `.gitignore` file also inlucded for `IntelliJ`.

### How to create project from the archetype

1. Install archetype to local maven repository

```bash
# In oneJarApp directory
mvn install
```

2. Create project from local maven archetype `com.tomdeng.archetypes:oneJarApp` from the IDE. For **IntelliJ IDEA**, a [**Maven Archetype Catalogs**](https://plugins.jetbrains.com/plugin/7965-maven-archetype-catalogs) plugin make it easy to load local archetype, simply add /Users/[username]/.m2/repository/archetype-catalog.xml to catalog. 
3. Or, create project by running command:

```bash
mvn archetype:generate -DarchetypeCalalog=local
```

### How to customize it

* Add your favorite library to **`src/main/resources/archetype-resources/pom.xml`**, NOT the `pom.xml` in root directory.
* Add addtional files in `src/main/resources/META-INF/maven/archetype-metadata.xml`

 ### Notes

To remove the jar-with-dependencies suffix from the built jar file name, set **<finalName>** and **<appendAssemblyId>false</appendAssemblyId>** in `src/main/resources/archetype-resources/pom.xml`

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <version>3.0.0</version>
    <configuration>
        <finalName>${project.artifactId}-${project.version}</finalName>
        <appendAssemblyId>false</appendAssemblyId>
        <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
        </descriptorRefs>
```

To remove Archetypes from IntelliJ IDEA 2020.2 on Mac

```bash
 rm -rf ~/Library/Caches/JetBrains/IdeaIC2020.2/Maven/Indices
```

**[Guide to Creating Archetypes](https://maven.apache.org/guides/mini/guide-creating-archetypes.html)**

To create an archetype project skeleton structure

```bash
mvn archetype:generate
 -DarchetypeGroupId=org.apache.maven.archetypes 
 -DarchetypeArtifactId=maven-archetype-archetype 
 -DarchetypeVersion=1.4
 -DgroupId=<your_groupID>
 -DartifactId=<your_artifactId>
 -Dversion=<your_artifact_version>
```

