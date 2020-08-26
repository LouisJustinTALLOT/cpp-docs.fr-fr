---
title: com_interface_entry (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 8339afb97df57f5080629dfed08823c5c091c5a3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844117"
---
# <a name="com_interface_entry-c"></a>com_interface_entry (C++)

Ajoute une entrée d’interface dans le mappage COM de la classe cible.

## <a name="syntax"></a>Syntaxe

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>Paramètres

*com_interface_entry*<br/>
Chaîne contenant le texte réel de l’entrée. Pour obtenir la liste des valeurs possibles, consultez [COM_INTERFACE_ENTRY macros](../../atl/reference/com-interface-entry-macros.md).

## <a name="remarks"></a>Notes

L’attribut **COM_INTERFACE_ENTRY** C++ insère le contenu non abrégé d’une chaîne de caractères dans le mappage d’interface com de l’objet cible. Si l’attribut est appliqué une seule fois à l’objet cible, l’entrée est insérée au début du mappage d’interface existant. Si l’attribut est appliqué de façon répétée au même objet cible, les entrées sont insérées au début de la carte d’interface dans l’ordre dans lequel elles sont reçues.

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliqué, `vi_progid` et `coclass` sont également appliqués.

Étant donné que la première utilisation de **COM_INTERFACE_ENTRY** entraîne l’insertion de la nouvelle interface au début du mappage d’interface, il doit s’agir de l’un des types de COM_INTERFACE_ENTRY suivants :

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

Des utilisations supplémentaires de l’attribut **COM_INTERFACE_ENTRY** peuvent utiliser tous les types de COM_INTERFACE_ENTRY pris en charge.

Cette restriction est nécessaire, car ATL utilise la première entrée dans le mappage d’interface comme identité `IUnknown` ; par conséquent, l’entrée doit être une interface valide. Par exemple, l’exemple de code suivant n’est pas valide, car la première entrée dans le mappage d’interface ne spécifie pas d’interface COM réelle.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>Exemple

Le code suivant ajoute deux entrées au mappage d’interface COM existant de `CMyBaseClass` . La première est une interface standard, tandis que la seconde masque l' `IDebugTest` interface.

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

Le mappage d’objet COM obtenu pour `CMyBaseClass` est le suivant :

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

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Repeatable Read**|Oui|
|**Attributs requis**|Une ou plusieurs des valeurs suivantes : `coclass` , `progid` ou `vi_progid` .|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)
