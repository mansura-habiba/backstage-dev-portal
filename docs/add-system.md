# Add System with different related component

Lets say I have a system that has an API, a SDK library and a Service as follows

![image](https://user-images.githubusercontent.com/26741425/226742823-d015e336-d5ee-457e-be0b-49831e4b651b.png)

Now I need to create all these component separately in our catalog. 

The [shuffle-api](https://github.com/backstage/backstage/blob/master/packages/catalog-model/examples/components/shuffle-api-component.yaml) will be in a yaml file with following content 

```
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: shuffle-api
  description: Shuffle API
  labels:
    goVersion: go1.15.3
    category: music
  tags:
    - go
spec:
  type: service
  lifecycle: production
  owner: user:guest
  system: audio-playback
```
![image](https://user-images.githubusercontent.com/26741425/226743682-23413fb3-62da-4643-b301-b1839834e1df.png)


The [playback-sdk](https://github.com/backstage/backstage/blob/master/packages/catalog-model/examples/components/playback-lib-component.yaml) will be in a yaml file with following content 

```
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: playback-sdk
  description: Audio and video playback SDK
spec:
  type: library
  lifecycle: experimental
  owner: team-c
  system: audio-playback
 ```
 
 
 ![image](https://user-images.githubusercontent.com/26741425/226743560-3e75f527-695f-4300-8edc-86cd0e44dcf7.png)

 
 And the (playback-order)[https://github.com/backstage/backstage/blob/master/packages/catalog-model/examples/components/playback-order-component.yaml] will be in a yaml file with following content 
 
 ```
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: playback-order
  description: Playback Order
  tags:
    - java
    - playback
spec:
  type: service
  lifecycle: production
  owner: user:guest
  system: audio-playback
  
  ```
  
  ![image](https://user-images.githubusercontent.com/26741425/226743938-609d8e5d-78f6-4401-85e3-d2be57caa046.png)


Now once I added all this items I need to add the system in a yaml file for (audio-playback)[https://github.com/backstage/backstage/blob/master/packages/catalog-model/examples/systems/audio-playback-system.yaml] System

```
apiVersion: backstage.io/v1alpha1
kind: System
metadata:
  name: audio-playback
  description: Audio playback system
spec:
  owner: team-c
  domain: playback

```

This system will have its ownership relation model as well as all listed omponent automatically appoear in its own page as follows

![image](https://user-images.githubusercontent.com/26741425/226744679-8cb150cc-8000-4a5e-8eb7-fb1cd84f1a20.png)
