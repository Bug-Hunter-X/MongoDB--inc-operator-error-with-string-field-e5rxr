# MongoDB $inc operator error with string field

This repository demonstrates an error that can occur when using the `$inc` operator in MongoDB update operations. The error arises when attempting to increment a field that is of string type instead of a numeric type.

## Bug

The following code snippet demonstrates the incorrect usage:

```javascript
// Incorrect usage of $inc operator with a string field
db.collection.updateOne({ _id: 1 }, { $inc: { "stringField": 1 } });
```

Attempting to execute this will result in an error because the `$inc` operator is designed for numeric fields.

## Solution

To fix this, ensure that the field you are attempting to increment using the `$inc` operator is of numeric type (int, long, or double). Alternatively, if the field needs to be string, use the `$set` operator to update the field.

The corrected code should look like this:
```javascript
// Correct usage of $inc operator with a numeric field
db.collection.updateOne({ _id: 1 }, { $inc: { "numericField": 1 } });
```