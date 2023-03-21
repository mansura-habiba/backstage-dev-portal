# Add Group to the Catalog 
Lets say I wantt to create a group with name *team-a*
1. I create a *Group* item in a yaml file named *team-a.yaml* with the following details. 
```
apiVersion: backstage.io/v1alpha1
kind: Group
metadata:
  name: team-a
  description: Team A
spec:
  type: team
  profile:
    # Intentional no displayName for testing
    email: team-a@example.com
    picture: https://avatars.dicebear.com/api/identicon/team-a@example.com.svg?background=%23fff&margin=25
  parent: backstage
  children: []
```
# Add User to the Catalog 

Now we need to add a user to the group
1. create a yaml file and add User kind of item with the following details 

```
apiVersion: backstage.io/v1alpha1
kind: User
metadata:
  name: breanna.davison
spec:
  profile:
    # Intentional no displayName for testing
    email: breanna-davison@example.com
    picture: https://avatars.dicebear.com/api/avataaars/breanna-davison@example.com.svg?background=%23fff
  memberOf: [team-a]
  ```
  # Add to app-config file 
  
  Now I have to add this new file *team-a.yaml* to my app-config file as follows 
  
  Either as a file location
  
  ```
      - type: file
      target: ../../examples/team-a.yaml
      rules:
        - allow: [User, Group]
  ```
  Or as a Git Repo URL
  
  ```
      - type: url
      target: https://github.com/backstage/backstage/blob/master/packages/catalog-model/contents/acme/team-a.yaml
      rules:
        - allow: [User, Group]
  ```
  
  Now if I go to my application and From teh filter menu choose "Group" I would see a new Group is created 
  
  <img width="1257" alt="image" src="https://user-images.githubusercontent.com/26741425/226740449-d9a114b6-6d9a-4f65-920f-128176bb8af9.png">

  If I go inside of the "team-a" from the list I would see teh users and other assets owned by this team or Group 
  
  <img width="1433" alt="image" src="https://user-images.githubusercontent.com/26741425/226740978-a1571caf-537d-46d6-a477-3504a85ce598.png">

  
  More example can be found [here](https://github.com/backstage/backstage/tree/master/packages/catalog-model/examples/acme).
