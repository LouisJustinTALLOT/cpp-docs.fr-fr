---
title: satype (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 255517789a5854ee6f76c4982bb75825905df546
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791004"
---
# <a name="satype"></a>satype

Spécifie le type de données de la `SAFEARRAY` structure.

## <a name="syntax"></a>Syntaxe

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Paramètres

*data_type*<br/>
Le type de données pour le `SAFEARRAY` structure de données qui est passé en tant que paramètre à une méthode d’interface.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

## <a name="remarks"></a>Notes

Le **satype** attribut C++ Spécifie le type de données de la `SAFEARRAY`.

> [!NOTE]
> Un niveau d’indirection est supprimé de la `SAFEARRAY` pointeur dans le fichier .idl généré à partir de la façon dont elle est déclarée dans le fichier .cpp.

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
[ID](id.md)  