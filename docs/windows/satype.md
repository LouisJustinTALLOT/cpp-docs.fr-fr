---
title: satype | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6562721cfdf1fb963a6af71e8a8665887fa4d4ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413103"
---
# <a name="satype"></a>satype

Spécifie le type de données de la `SAFEARRAY` structure.

## <a name="syntax"></a>Syntaxe

```cpp
[ satype(
   data_type
) ]
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

[Attributs de compilateur](../windows/compiler-attributes.md)<br/>
[Attributs de paramètres](../windows/parameter-attributes.md)<br/>
[Attributs de méthode](../windows/method-attributes.md)<br/>
[ID](../windows/id.md)  