---
title: satype (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 4619deec6d5e4e9083fbc7bcab53caee0101285c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166274"
---
# <a name="satype"></a>satype

Spécifie le type de données de la structure `SAFEARRAY`.

## <a name="syntax"></a>Syntaxe

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Paramètres

*data_type*<br/>
Type de données pour la structure de données `SAFEARRAY` qui est passée en tant que paramètre à une méthode d’interface.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

## <a name="remarks"></a>Notes

L’attribut **satype** C++ spécifie le type de données du `SAFEARRAY`.

> [!NOTE]
> Un niveau d’indirection est supprimé du pointeur `SAFEARRAY` dans le fichier. idl généré à partir de la manière dont il est déclaré dans le fichier. cpp.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[id](id.md)
