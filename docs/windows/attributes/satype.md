---
description: 'En savoir plus sur : satype'
title: satype (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: dab0f866eba5501a9a83d531d9cbdf50501dcff0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327322"
---
# <a name="satype"></a>satype

Spécifie le type de données de la `SAFEARRAY` structure.

## <a name="syntax"></a>Syntaxe

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Paramètres

*data_type*<br/>
Type de données pour la `SAFEARRAY` structure de données qui est passée en tant que paramètre à une méthode d’interface.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

## <a name="remarks"></a>Notes

L’attribut **satype** C++ spécifie le type de données de `SAFEARRAY` .

> [!NOTE]
> Un niveau d’indirection est supprimé du `SAFEARRAY` pointeur dans le fichier. idl généré de la manière dont il est déclaré dans le fichier. cpp.

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

[Attributs du compilateur](compiler-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[id](id.md)
