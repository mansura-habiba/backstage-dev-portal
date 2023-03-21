# Add Docuemntation to the Catalog
1. Create a Component with following details 
```
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: sample-component
  title : Sample Component with Documentation
  description: >
    This is a sample component with documenattion
  ownership:
    team: team-a
    directorate: Team A

  annotations:
    backstage.io/techdocs-ref: dir:.
spec:
  type: service
  lifecycle: production
  owner: guest
  dependsOn: ['component:audio-playback']
```

Make sure to add the following 

```
annotations:
    backstage.io/techdocs-ref: dir:.
```

So the docker engine will look for the *mkdocs.yml* file in the same directory of the yaml file with the definition of the component.

Put a mkdoc.yaml file in the same directory

```
site_name: ${{values.component_id}}
site_description: ${{values.description}}

nav:
  - Introduction: index.md

plugins:
  - techdocs-core
  
 ```
 If we add more menu we  can add more items under the **nav** same as *introduction*
 
 In teh same folder create a folder call 'docs' and put the index.md file in that folder 
 
 ```
 ---
layout: doc
title: Sample Component for Docuemnattion
date: 2019-09-08 8:14:30 +0600
tags: [Manage]
toc: true
---
# Overview
Eget velit aliquet sagittis id consectetur purus ut faucibus. Tortor condimentum lacinia quis vel. Morbi quis commodo odio aenean sed adipiscing diam. Ac odio tempor orci dapibus ultrices. Sit amet est placerat in. Molestie nunc non blandit massa enim nec dui nunc mattis. Facilisis mauris sit amet massa vitae. Sit amet risus nullam eget felis eget nunc lobortis. Nunc mattis enim ut tellus elementum. Ultrices tincidunt arcu non sodales neque sodales. Feugiat in fermentum posuere urna nec tincidunt. Tempus imperdiet nulla malesuada pellentesque elit eget gravida. Ipsum suspendisse ultrices gravida dictum fusce ut placerat. Et netus et malesuada fames ac turpis egestas. Facilisis sed odio morbi quis commodo odio aenean sed.

# Heading 3
Eget egestas purus viverra accumsan in nisl. Aliquam sem fringilla ut morbi tincidunt augue interdum. Lorem donec massa sapien faucibus. Cras adipiscing enim eu turpis egestas pretium. Turpis massa tincidunt dui ut. Id velit ut tortor pretium viverra suspendisse potenti nullam. Amet nisl purus in mollis nunc sed id. Auctor eu augue ut lectus arcu bibendum. Venenatis lectus magna fringilla urna porttitor rhoncus dolor purus non. Facilisis magna etiam tempor orci. Ante in nibh mauris cursus mattis molestie a. Eget mauris pharetra et ultrices neque. Porttitor leo a diam sollicitudin tempor id eu nisl nunc. Nunc faucibus a pellentesque sit amet porttitor eget dolor.

# Heading 4
Aliquet nibh praesent tristique magna sit amet purus gravida. Viverra nibh cras pulvinar mattis. Et molestie ac feugiat sed lectus vestibulum mattis ullamcorper. Est ultricies integer quis auctor. Tellus mauris a diam maecenas sed. Risus viverra adipiscing at in tellus. Id diam maecenas ultricies mi eget mauris pharetra et ultrices. Netus et malesuada fames ac turpis egestas maecenas pharetra. Justo laoreet sit amet cursus sit amet dictum. Volutpat maecenas volutpat blandit aliquam etiam erat velit scelerisque in. Ornare quam viverra orci sagittis eu volutpat. Netus et malesuada fames ac turpis. Eu nisl nunc mi ipsum faucibus vitae. In fermentum posuere urna nec tincidunt praesent semper feugiat. Lacus sed turpis tincidunt id aliquet risus feugiat. Egestas fringilla phasellus faucibus scelerisque eleifend donec.

# Heading 5
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Auctor elit sed vulputate mi sit. At urna condimentum mattis pellentesque id nibh tortor id aliquet. Massa massa ultricies mi quis hendrerit dolor. Suspendisse sed nisi lacus sed. Fames ac turpis egestas sed tempus urna et. Pharetra diam sit amet nisl suscipit adipiscing bibendum est ultricies. Nec ullamcorper sit amet risus. Tempor orci dapibus ultrices in iaculis nunc. Sed blandit libero volutpat sed cras. Ut tortor pretium viverra suspendisse potenti. Sit amet luctus venenatis lectus magna fringilla urna porttitor. Sed augue lacus viverra vitae congue. Amet cursus sit amet dictum sit. Adipiscing at in tellus integer feugiat scelerisque varius. Quis ipsum suspendisse ultrices gravida dictum fusce ut placerat. Eu lobortis elementum nibh tellus molestie nunc. Amet tellus cras adipiscing enim eu turpis egestas. Quam viverra orci sagittis eu volutpat.


```

Keep the docker running on teh machine 

Now run the application with the command 

```
yarn dev
```

Go to Docs from the Navigation menu and we can see the docuemnattion catalog is there 

![image](https://user-images.githubusercontent.com/26741425/226749471-15fe7d93-6ace-41cb-b8cc-5eba67033eab.png)



And if we click on the item , it will take some time to build for the first time . We need to make sure that the docker is running and we will see teh docuemnt there


![image](https://user-images.githubusercontent.com/26741425/226750253-40db8ba8-8b74-4cab-971c-5165e319df02.png)


  
