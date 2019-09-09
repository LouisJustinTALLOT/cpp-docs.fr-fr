---
title: ProgID (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: d529d7362dc62207cfd72576159f560a3e04c221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514252"
---
# <a name="progid"></a>progid

Spécifie le ProgID d’un objet COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Paramètres

*name*<br/>
ProgID représentant l’objet.

Les ProgID présentent une version explicite de l’identificateur de classe (CLSID) utilisé pour identifier les objets COM/ActiveX.

## <a name="remarks"></a>Notes

L’attribut **ProgID** C++ vous permet de spécifier le ProgID d’un objet com. Un ProgID se présente sous la forme *nom1. nom2. version*. Si vous ne spécifiez pas de *version* pour un ProgID, la version par défaut est 1. Si vous ne spécifiez pas *nom1. nom2*, le nom par défaut est *className. ClassName*. Si vous ne spécifiez pas **ProgID** et que vous `vi_progid`spécifiez, *nom1. nom2* est `vi_progid` pris de et la version (numéro séquentiel suivant) est ajoutée.

Si un bloc d’attributs qui utilise **ProgID** n’utilise pas également **UUID**, le compilateur vérifie le registre pour déterminer s’il existe un **UUID** pour le **ProgID**spécifié. Si **ProgID** n’est pas spécifié, la version (et le nom de la coclasse, si la création d’une coclasse) sera utilisée pour générer un **ProgID**.

**ProgID** implique l' `coclass` attribut, autrement dit, si vous spécifiez **ProgID**, c’est la même chose que la `coclass` spécification des attributs et **ProgID** .

L’attribut **ProgID** provoque l’inscription automatique d’une classe sous le nom spécifié. Le fichier. idl généré n’affiche pas la valeur **ProgID** .

Lorsque cet attribut est utilisé dans un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement ci-dessus, les informations spécifiées avec cet attribut sont utilisées dans `GetProgID` la fonction, injectées par `coclass` l’attribut. Pour plus d’informations, consultez l’attribut [coclass](coclass.md) .

## <a name="example"></a>Exemples

Consultez l’exemple de [coclass](coclass.md) pour obtenir un exemple d’utilisation du **ProgID**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Clé ProgID](/windows/win32/com/-progid--key)
