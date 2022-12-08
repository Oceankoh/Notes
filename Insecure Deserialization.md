# Java

## Controllable variables/attributes in serialized objects

All objects attributes are controllable unless they are marked as `transient`. `transient` attributes are not serialized.

## Methods called during deserialization 

When an object is deserialized in Java, the following methods are executed, if they exist:

1.  The `private void readObject(ObjectInputStream inputStream) throws IOException, ClassNotFoundException` method, if it is defined and marked as `private`. This method is used to initialize the object by reading its serialized state from the input stream.
2.  The `private void readObjectNoData() throws ObjectStreamException` method, if it is defined and marked as `private`. This method is called when the object is deserialized and no data is available in the input stream to initialize the object.
3.  The `void readResolve() throws ObjectStreamException` method, if it is defined. This method is called after the object has been deserialized and allows the object to replace itself with a new instance that is returned by this method.

Note that the `readObject` and `readObjectNoData` methods are not called if the `readResolve` method is defined and returns a non-null value. In that case, the returned object is used as the deserialized object and the `readObject` and `readObjectNoData` methods are not called.

## Serialization format

Java objects are serialized with the [Object Serialization Stream Protocol](https://docs.oracle.com/javase/8/docs/platform/serialization/spec/protocol.html) . 

```
ac ed 00 05 73 72 00 23 64 61 74 61 2e 70 72 6f 64 75 63 74 63 61 74 61 6c 6f 67 2e 50 72 6f 64 75 63 74 54 65 6d 70 6c 61 74 65 00 00 00 00 00 00 00 01 02 00 01 4c 00 02 69 64 74 00 12 4c 6a 61 76 61 2f 6c 61 6e 67 2f 53 74 72 69 6e 67 3b 78 70 74 00 01 27
```

The given serialized object represents a Java object of the class `data.productcatalogue.ProductTemplate`. The object has two fields: an `id` field of type `String`, and a `product` field of type `Product`.

The serialized object consists of the following data blocks:

-  The `ac ed` bytes at the beginning of the object indicate that it is a serialized Java object, and the `00 05` bytes indicate that it uses the latest version of the Java serialization format.
-  The `73` block indicates that the next block is a `TC_OBJECT` block, which represents the actual object.
-  The `72 00 23` block indicates that the next block is a `TC_CLASSDESC` block, with a length of 35 bytes. This block describes the class of the object.
-  The `64 61 74 61 2e 70 72 6f 64 75 63 74 63 61 74 61 6c 6f 67 2e 50 72 6f 64 75 63 74 54 65 6d 70 6c 61 74 65` block represents the fully-qualified class name of the object (i.e., `data.productcatalogue.ProductTemplate`).
-  The `00 00 00 00 00 00 00 01` block indicates that the class has one field.
-  The `02` block indicates that the field is of type `ObjectStreamField.TYPE_OBJECT`.
-  The `00 01` block indicates that the field is not `transient` or `static`.
-  The `4c 00 02 69 64` block represents the length of name and name the field (`id`).
-  The `74` represents type `String` of length `00 12` encoding the attribute type `java/lang/String`
- Finally, the value of the string of length `00 001` is `''` 

# PHP 

## Magic Methods

All methods names starting with `__` are reserved by PHP. 

## `__sleep()`

`serialize()` checks if the class has a function with the magic name` __sleep()`. If so, that function is executed prior to any serialization. It can clean up the object and is supposed to return an array with the names of all variables of that object that should be serialized. If the method doesn't return anything then null is serialized and `E_NOTICE` is issued. 

## `__wakeup()`

Conversely, `unserialize()` checks for the presence of a function with the magic name` __wakeup()`. If present, this function can reconstruct any resources that the object may have. 

## `__destruct()`

A destructor is called when the object is destructed or the script is stopped or exited. If you create a __destruct() function, PHP will automatically call this function at the end of the script.

## `__serialize()`

Very similar to `__sleep()`. However, if both are defined, this will take precedence. 

## `__unserialize()`

Very similar to `__wakeup()`. However, if both are defined, this will take precedence. 

## `__get()`

This triggers when an inaccessible variable is called. E.g. when the code tries to retrieve the value of a private variable of an object, the `__get()` function of the object will be called (if defined). 

## Controllable attributes

All attributes are controllable regardless of whether they are marked `public` or `private`. Object's private members have the class name prepended to the member name; protected members have a `*` prepended to the member name. These prepended values have null bytes on either side. These prepended values can be ignored. In other words, when crafting a payload, mark all memebrs as public. 

