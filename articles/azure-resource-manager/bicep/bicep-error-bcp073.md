---
title: BCP073
description: Warning - The property <property-name> is read-only. Expressions cannot be assigned to read-only properties.
ms.topic: reference
ms.custom: devx-track-bicep
ms.date: 07/15/2024
---

# Bicep warning code - BCP073

This warning occurs when you assign a value to a read-only property.

## Warning description

`The property <property-name> is read-only. Expressions cannot be assigned to read-only properties.`

## Solution

Remove the property assignment from the file.  

## Examples

The following example raises the warning because `sku` can only be set on the `storageAccounts` level. It is read-only for services that are under a storage account like `blobServices` and `fileServices`.

```bicep
param location string

resource storage 'Microsoft.Storage/storageAccounts@2023-04-01' = {
  name: 'mystore'
  location: location
  sku: {
    name: 'Standard_LRS'
  }
  kind:  'StorageV2'
}

resource blobService 'Microsoft.Storage/storageAccounts/blobServices@2023-04-01' = {
  parent: storage
  name: 'default'
  sku: {}
}
```

You can fix the issue by removing the `sku` property assignment:

```bicep
param location string

resource storage 'Microsoft.Storage/storageAccounts@2023-04-01' = {
  name: 'mystore'
  location: location
  sku: {
    name: 'Standard_LRS'
  }
  kind:  'StorageV2'
}

resource blobService 'Microsoft.Storage/storageAccounts/blobServices@2023-04-01' = {
  parent: storage
  name: 'default'
}
```

## Next steps

For more information about Bicep error and warning codes, see [Bicep warnings and errors](./bicep-error-codes.md).