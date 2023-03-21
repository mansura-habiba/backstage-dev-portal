# Add API to the Catalog

When backstage application is crated locally it usually add a sample API to the file 


```
apiVersion: backstage.io/v1alpha1
kind: API
metadata:
  name: example-grpc-api
spec:
  type: grpc
  lifecycle: experimental
  owner: guests
  system: examples
  definition: |
    syntax = "proto3";

    service Exampler {
      rpc Example (ExampleMessage) returns (ExampleMessage) {};
    }

    message ExampleMessage {
      string example = 1;
    };

```

This is added to the **app-config.yaml** file  as follows

```
  locations:
    # Local example data, file locations are relative to the backend process, typically `packages/backend`
    - type: file
      target: ../../examples/entities.yaml
  ```
  
  We can add more detailed APi defnition like this [one](https://github.com/backstage/backstage/blob/master/packages/catalog-model/examples/apis/hello-world-api.yaml)
  
  ```
  apiVersion: backstage.io/v1alpha1
kind: API
metadata:
  name: hello-world
  description: Hello World example for gRPC
spec:
  type: grpc
  lifecycle: deprecated
  owner: team-c
  definition: |
    // Copyright 2015 gRPC authors.
    //
    // Licensed under the Apache License, Version 2.0 (the "License");
    // you may not use this file except in compliance with the License.
    // You may obtain a copy of the License at
    //
    //     http://www.apache.org/licenses/LICENSE-2.0
    //
    // Unless required by applicable law or agreed to in writing, software
    // distributed under the License is distributed on an "AS IS" BASIS,
    // WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    // See the License for the specific language governing permissions and
    // limitations under the License.
    syntax = "proto3";
    option java_multiple_files = true;
    option java_package = "io.grpc.examples.helloworld";
    option java_outer_classname = "HelloWorldProto";
    option objc_class_prefix = "HLW";
    package helloworld;
    // The greeting service definition.
    service Greeter {
      // Sends a greeting
      rpc SayHello (HelloRequest) returns (HelloReply) {}
    }
    // The request message containing the user's name.
    message HelloRequest {
      string name = 1;
    }
    // The response message containing the greetings
    message HelloReply {
      string message = 1;
    }
  ```
  
  More example can be found [here](https://github.com/backstage/backstage/tree/master/packages/catalog-model/examples/apis/)
  OR Any Open API [like this one](https://github.com/backstage/backstage/blob/master/packages/catalog-model/examples/apis/spotify-api.yaml)
  
  ```
  apiVersion: backstage.io/v1alpha1
kind: API
metadata:
  name: spotify
  description: The Spotify web API
  tags:
    - spotify
    - rest
  annotations:
    # The annotation is deprecated, we use placeholders (see below) instead, remove it later.
    backstage.io/definition-at-location: 'url:https://raw.githubusercontent.com/APIs-guru/openapi-directory/master/APIs/spotify.com/v1/swagger.yaml'
spec:
  type: openapi
  lifecycle: production
  owner: team-a
  definition:
    $text: https://github.com/APIs-guru/openapi-directory/blob/dab6854d4d599aafb0eb36e6c7ae1fe0c37509b7/APIs/spotify.com/2021.4.2/openapi.yaml
    ```
    
  
  Once this yaml files are added to the app-config.yaml file they will be available to the catalog with swagger docuemnattion. For example 
  
  ![image](https://user-images.githubusercontent.com/26741425/226742043-e1571751-216b-4db0-ba01-11ac31dd30e2.png)

  
