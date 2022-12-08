# Alfresco docker deployment

[Source] (https://docs.alfresco.com/content-services/community/install/containers/docker-compose/)
[Source] (https://docs.alfresco.com/content-services/6.0/admin/metadata-extraction/)
[Source] (https://docs.alfresco.com/content-services/5.2/admin/import-transfer/)



1. Clone the project locally, and change directory to the project’s `docker-compose` folder:

```
 git clone https://github.com/Alfresco/acs-deployment.git
 cd acs-deployment/docker-compose
```

2.   Deploy Community Edition, including the repository, Share, Postgres database, Search Services, etc.:

```
 docker-compose -f community-docker-compose.yml up
```

3. Open your browser and check everything starts up correctly:

| Service                        | Endpoint                            |
| ------------------------------ | ----------------------------------- |
| Administration and REST APIs   | `http://localhost:8080/alfresco`    |
| Share                          | `http://localhost:8080/share`       |
| Alfresco Content App           | `http://localhost:8080/content-app` |
| Search Services administration | `http://localhost:8083/solr`        |

## Import files

1. Access container and create import folder

```bash
docker exec -ti alfresco/alfresco-content-repository-community:7.3.0
$ mkdir /tmp/import
```

2. Copy files to import folder

3. Use web app to start import
   
```url
http://localhost:8080/alfresco/service/bulkfsimport
```
   
```
Import directory: /tmp/import
Target space: /
```
   
4. Initiate bulk import



Sample metadata for file SEI.pdf

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE properties SYSTEM "http://java.sun.com/dtd/properties.dtd">
<properties>
    <entry key="type">cm:content</entry>
    <entry key="aspects">cm:versionable,cm:dublincore</entry>
    <entry key="cm:title">A photo of a flower.</entry>
    <entry key="cm:description">A photo I took of a flower while walking around Bantry Bay.</entry>
  </properties>
```


