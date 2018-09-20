---
title: nonbrowsable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonbrowsable
dev_langs:
- C++
helpviewer_keywords:
- nonbrowsable attribute
ms.assetid: e71a98e7-4b65-454a-9829-342b9f2a84be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e8527f2d35de6591bf49f0fd32cc0df64a059e02
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371938"
---
# <a name="nonbrowsable"></a>nonbrowsable

Indique qu’un membre d’interface ne doit pas être affiché dans un Explorateur de propriétés.

## <a name="syntax"></a>Syntaxe

```cpp
[nonbrowsable]
```

## <a name="remarks"></a>Notes

Le **nonbrowsable** attribut C++ a les mêmes fonctionnalités que le [nonbrowsable](/windows/desktop/Midl/nonbrowsable) attribut MIDL.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_nonbrowsable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, helpstring("help string"), helpstringcontext(1),
uuid="11111111-1111-1111-1111-111111111111"]
__interface IMyI
{
   [nonbrowsable] HRESULT xx();
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs de méthode](../windows/method-attributes.md)  