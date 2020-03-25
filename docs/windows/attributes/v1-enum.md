---
title: v1_enum (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 1a189f6f1c5ef9d4ae77df9f1eda3f3671ddaf52
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166105"
---
# <a name="v1_enum"></a>v1_enum

Indique que le type énuméré spécifié doit être transmis en tant qu’entité 32 bits au lieu de la valeur par défaut 16 bits.

## <a name="syntax"></a>Syntaxe

```cpp
[v1_enum]
```

## <a name="remarks"></a>Notes

L’attribut **v1_enum** C++ a les mêmes fonctionnalités que l’attribut MIDL [v1_enum](/windows/win32/Midl/v1-enum) .

## <a name="example"></a>Exemple

Le code suivant illustre une utilisation de **v1_enum**:

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Type énuméré|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)
