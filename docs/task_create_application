# Task 1 : Create Application 

## Install Software 

1. Nodejs 
2. any IDE
3. Github

## Create Application 

1. Open the terminal and run the follloowing command 

```
npx @backstage/create-app
```

This will create a new Backstage App inside the current folder. The name of the app-folder is the name that was provided when prompted.

![](https://backstage.io/assets/images/create-app_output-aae53df8840c4eb4413b2e0d22248db5.png)

Intiially it will ask to install *backstage/create-app* package 


```
Need to install the following packages:
  @backstage/create-app
Ok to proceed? (y) 
```


## Details of the file created

1. *app-config.yaml:* Main configuration file for the app. See Configuration for more information.
2. *catalog-info.yaml:* Catalog Entities descriptors. See Descriptor Format of Catalog Entities to get started.
lerna.json: Contains information about workspaces and other lerna configuration needed for the monorepo setup.
3. *package.json:* Root package.json for the project. Note: Be sure that you don't add any npm dependencies here as they probably should be installed in the intended workspace rather than in the root.
4. *packages/:* Lerna leaf packages or "workspaces". Everything here is going to be a separate package, managed by lerna.
5. *packages/app/:* An fully functioning Backstage frontend app, that acts as a good starting point for you to get to know Backstage.
6. *packages/backend/:* We include a backend that helps power features such as Authentication, Software Catalog, Software Templates and TechDocs amongst other things.


More Details can be found in [here](https://backstage.io/docs/getting-started/create-an-app)

## TroubleShoot 

### Node Version
Nodejs version should be 16|| 18
```
  executing     yarn install ◝ error root@1.0.0: The engine "node" is incompatible with this module. Expected version "16 || 18". Got "14.18.2"
 ````

