## A maven archetype for creating a war packaged JSF web app

### Why create one

JSF is much less popular as Springboot. I could not find one fits me so create this one to save tone of boilerplate process. It's base on Java 8 and EE 7. 

### The structure

* `main/java` holds java codes, `main/webapp` holds xhtml files
* Libraries included:
  * gson
  * log4j/slf4j
  * lombok
  * mysql
  * apache commons-lang3
  * sql2o
* The `index.xhtml` uses `template.xhtml` as parent template, which include `Bootstrap 4`
* `.gitignore` included.

### How to create project from the archetype

1. Install archetype to local maven repository

```bash
# In jsf directory
mvn install
```

2. Create project from local maven archetype `com.tomdeng.archetypes:jsf from the IDE. For **IntelliJ IDEA**, a [**Maven Archetype Catalogs**](https://plugins.jetbrains.com/plugin/7965-maven-archetype-catalogs) plugin make it easy to load local archetype, simply add /Users/[username]/.m2/repository/archetype-catalog.xml to catalog. 
3. Or, create project by running command:

```bash
mvn archetype:generate -DarchetypeCalalog=local
```

### How to customize it

* Add your favorite library to **`src/main/resources/archetype-resources/pom.xml`**, NOT the `pom.xml` in root directory.
* Add addtional files in `src/main/resources/META-INF/maven/archetype-metadata.xml`

### Remained Issues

* I could not put `##version_number` as war file suffix in `pom.xml`. 
* Tried to inlcude the empty sub directories by adding `<includeEmptyDirs>true</includeEmptyDirs>` to `maven-resources-plugin` but no luck