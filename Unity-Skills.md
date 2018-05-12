#Unity Coding Skills

### Instantiate

####Instantiate Object

```c#
// Load instantiate prefab, prefab should put into the /Assets/Resoureces folder!
var prefabObject = Resources.Load<GameObject>("prefabName");

// Instantiate object to specific position
GameObject instantiateObject = Instantiate(prefabObject, new Vector3(posX, posY, posZ), Quaternion.identity);
```

####Set the instantiate object's name

```c#
instantiateObject.name = customizeName;
```

#### Set the instantiate object's parent

```c#
instantiateObject.transform.parent = parentName.transform;
```

