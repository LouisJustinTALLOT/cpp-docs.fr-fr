---
title: vi_progid (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 468b5c5dcadc1715384684062f203ae9179ef044
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791017"
---
# <a name="viprogid"></a>vi_progid

Spécifie un formulaire indépendant de la version du ProgID.

## <a name="syntax"></a>Syntaxe

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Paramètres

*name*<br/>
Le ProgID indépendants de la version qui représente l’objet.

ProgID présentent une version explicite de l’identificateur de classe (CLSID) utilisé pour identifier les objets COM/ActiveX.

## <a name="remarks"></a>Notes

Le **vi_progid** attribut C++ vous permet de spécifier un ProgID indépendants de la version pour un objet COM. Un ProgID présente sous la forme *name1.name2.version*. Un ProgID indépendants de la version n’a pas un *version*. Il est possible de spécifier à la fois le `progid` et **vi_progid** attributs sur un `coclass`. Si vous ne spécifiez pas **vi_progid**, le ProgID indépendants de la version est la valeur spécifiée par le [progid](progid.md) attribut.

**vi_progid** implique la `coclass` d’attribut, autrement dit, si vous spécifiez **vi_progid**, il est la même chose que si vous définissiez le `coclass` et **vi_progid** attributs.

Le **vi_progid** attribut entraîne une classe soit automatiquement inscrite sous le nom spécifié. Le fichier .idl généré n’affichera pas la valeur ProgID.

Dans les projets ATL, si le [coclasse](coclass.md) attribut est également présent, le ProgID spécifié est utilisé par le `GetVersionIndependentProgID` (fonction) (insérées par les `coclass` attribut).

## <a name="example"></a>Exemple

Consultez le [coclasse](coclass.md) exemple pour un exemple d’utilisation de **vi_progid**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Clé de progID](/windows/desktop/com/-progid--key)  
