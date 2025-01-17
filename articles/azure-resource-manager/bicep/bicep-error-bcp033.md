---
title: BCP033
description: Error/warning - Expected a value of type <data-type> but the provided value is of type <data-type>.
ms.topic: reference
ms.custom: devx-track-bicep
ms.date: 07/15/2024
---

# Bicep error/warning code - BCP033

This error/warning occurs when you assign a value of a mismatched data type.

## Error/warning description

`Expected a value of type <data-type> but the provided value is of type <data-type>.`

## Solution

Use the expected data type.  

## Examples

The following example raises the error because the expected data type is a string. The actual provided value is an integer:

```bicep
var myValue = 5

output myString string = myValue
```

You can fix the error by providing a string value:

```bicep
var myValue = '5'

output myString string = myValue
```

## Next steps

For more information about Bicep error and warning codes, see [Bicep warnings and errors](./bicep-error-codes.md).