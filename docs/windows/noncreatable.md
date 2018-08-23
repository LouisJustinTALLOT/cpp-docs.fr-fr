---
title: noncreatable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.noncreatable
dev_langs:
- C++
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a55daa9f8c742d847944ddb0459db208c7edf9cf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608122"
---
# <a name="noncreatable"></a>noncreatable

Définit un objet qui ne peut pas être instancié par lui-même.

## <a name="syntax"></a>Syntaxe

```cpp
[noncreatable]
```

## <a name="remarks"></a>Notes

Le **noncreatable** attribut C++ a les mêmes fonctionnalités que le [noncreatable](http://msdn.microsoft.com/library/windows/desktop/aa367118) attribut MIDL et est automatiquement transféré vers le texte généré. Fichier IDL par le compilateur.

Lorsque cet attribut est utilisé au sein d’un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement décrit ci-dessus, l’attribut injecte également le [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro. Cette macro indique à ATL que l’objet ne peut pas être créé en externe.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclass**|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs de classe](../windows/class-attributes.md)  
