---
title: Platform::TypeCode Enumeration | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::TypeCode
dev_langs:
- C++
helpviewer_keywords:
- Platform::TypeCode Enumeration
ms.assetid: 93c1305f-eb16-4bec-aead-f88d9518b4cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb19a922655a77a2f7a2b5806c9b721f17e028f8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104171"
---
# <a name="platformtypecode-enumeration"></a>Platform::TypeCode (énumération)

Spécifie une catégorie numérique qui représente un type intégré.

## <a name="syntax"></a>Syntaxe

```cpp
enum class TypeCode {};
```

### <a name="members"></a>Membres

|Code de type|Description|
|---------------|-----------------|
|Booléen|Type Platform::Boolean.|
|Char16|Type default::char16.|
|DateTime|Type DateTime.|
|Decimal|Type numérique.|
|Double|Type default::float64.|
|Empty|Void|
|Int16|Type default::int16.|
|Int32|Type default::int32.|
|Int64|Type default::int64.|
|Int8|Type default::int8.|
|Object|Type Platform::Object.|
|Single|Type default::float32.|
|Chaîne|Type Platform::String.|
|UInt16|Type default::uint16.|
|UInt32|Type default::uint32.|
|UInt64|Type default::uint64.|
|UInt8|Type default::uint8.|

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd