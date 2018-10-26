---
title: ProgID (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 239f50011c91320c2b5e0a96449139e8eeab10ff
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072861"
---
# <a name="progid"></a>progid

Spécifie le ProgID pour un objet COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Paramètres

*name*<br/>
Le ProgID qui représente l’objet.

ProgID présentent une version explicite de l’identificateur de classe (CLSID) utilisé pour identifier les objets COM/ActiveX.

## <a name="remarks"></a>Notes

Le **progid** attribut C++ vous permet de spécifier le ProgID pour un objet COM. Un ProgID présente sous la forme *name1.name2.version*. Si vous ne spécifiez pas un *version* pour un ProgID, la version par défaut est 1. Si vous ne spécifiez pas *name1.name2*, le nom par défaut est *classname.classname*. Si vous ne spécifiez pas **progid** et vous spécifiez `vi_progid`, *name1.name2* proviennent de `vi_progid` et (numéro séquentiel suivant) version est ajoutée.

Si un bloc d’attributs qui utilise **progid** n’utilise pas également **uuid**, le compilateur doit rechercher le Registre pour voir si un **uuid** existe pour le texte spécifié **progid** . Si **progid** n’est pas spécifié, la version (et le nom de la coclasse, si la création d’une coclasse) seront utilisés pour générer un **progid**.

**ProgID** implique la `coclass` d’attribut, autrement dit, si vous spécifiez **progid**, il est la même chose que si vous définissiez le `coclass` et **progid** attributs.

Le **progid** attribut entraîne une classe soit automatiquement inscrite sous le nom spécifié. Le fichier .idl généré n’affichera pas le **progid** valeur.

Lorsque cet attribut est utilisé au sein d’un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement décrit ci-dessus, les informations spécifiées avec cet attribut sont utilisées dans le `GetProgID` fonction, injectée par le `coclass` attribut. Pour plus d’informations, consultez le [coclasse](coclass.md) attribut.

## <a name="example"></a>Exemple

Consultez l’exemple de [coclasse](coclass.md) pour un exemple d’utilisation de **progid**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Clé de progID](/windows/desktop/com/-progid--key)
