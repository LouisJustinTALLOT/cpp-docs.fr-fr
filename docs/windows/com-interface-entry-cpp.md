---
title: COM_INTERFACE_ENTRY (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.com_interface_entry
dev_langs:
- C++
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 555dcfe83ab114db48942a5be604ff344dafa8ed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398715"
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)

Ajoute une entrée de l’interface dans le mappage COM de la classe cible.

## <a name="syntax"></a>Syntaxe

```cpp
[ com_interface_entry(
  com_interface_entry
) ]
```

### <a name="parameters"></a>Paramètres

*COM_INTERFACE_ENTRY*<br/>
Chaîne contenant le texte de l’entrée. Pour obtenir la liste des valeurs possibles, consultez [Macros COM_INTERFACE_ENTRY](../atl/reference/com-interface-entry-macros.md).

## <a name="remarks"></a>Notes

Le **com_interface_entry** attribut C++ insère le contenu ondes ultracourtes d’une chaîne de caractères dans la table d’interface COM de l’objet cible. Si l’attribut est appliqué une fois à l’objet cible, l’entrée est insérée au début de la carte d’interface existante. Si l’attribut est appliqué à plusieurs reprises pour le même objet cible, les entrées sont insérées au début de la carte d’interface dans l’ordre de que leur réception.

Cet attribut exige que l’attribut [coclass](../windows/coclass.md), [progid](../windows/progid.md)ou [vi_progid](../windows/vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliquée, `vi_progid` et `coclass` sont également appliquées.

Étant donné que la première utilisation de **com_interface_entry** provoque la nouvelle interface doit être inséré au début de la carte d’interface, il doit être un des types COM_INTERFACE_ENTRY suivants :

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

Utilisations supplémentaires de la **com_interface_entry** attribut peut utiliser les types de COM_INTERFACE_ENTRY tout pris en charge.

Cette restriction est nécessaire car ATL utilise la première entrée dans la table d’interface en tant que l’identité `IUnknown`; par conséquent, l’entrée doit être une interface valide. Par exemple, l’exemple de code suivant n’est pas valide, car la première entrée dans la table d’interface ne spécifie pas une interface COM réelle.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>Exemple

Le code suivant ajoute deux entrées à la carte d’interface COM existante de `CMyBaseClass`. La première est une interface standard, et le second masque le `IDebugTest` interface.

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")  
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

Mappage résultant de l’objet COM pour `CMyBaseClass` se présente comme suit :

```cpp
BEGIN_COM_MAP(CMyClass)  
    COM_INTERFACE_ENTRY (IMyClass)  
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)  
    COM_INTERFACE_ENTRY(IMyClass)  
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)  
    COM_INTERFACE_ENTRY(IDebugTest)  
    COM_INTERFACE_ENTRY(IProvideClassInfo)  
END_COM_MAP()  
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Oui|
|**Attributs requis**|Un ou plusieurs des opérations suivantes : `coclass`, `progid`, ou `vi_progid`.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs COM](../windows/com-attributes.md)<br/>
[Attributs de classe](../windows/class-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)  