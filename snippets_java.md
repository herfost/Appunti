# Snippets Java

## Serialize Object
Si premette che 
- outputStream implements OutputStream;
- object implements Serializable;
- fileOutputStream implements OutputStream
```java

ObjectOutputStream objectOutputStream = new ObjectOutputStrem(outputStream);
objectOutputStream.writeObject(object)
```

## byte[] from Object
```java
ByteArrayOutputStream byteArrayOutputStream = new ByteArrayOutputStream();
ObjectOutputStream objectOutputStream = new(byteArrayOutputStream);

objectOutputStream.writeObject(object);
byte[] objectBytes = byteArrayOutputStream.toByteArray();
```