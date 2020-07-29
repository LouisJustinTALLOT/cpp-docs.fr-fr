---
title: ProgID (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: 3092111236afe1e1360a2814c3091ab0de4ff6ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213851"
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

L' `progid` attribut C++ vous permet de spécifier le ProgID d’un objet com. Un ProgID se présente sous la forme *nom1. nom2. version*. Si vous ne spécifiez pas de *version* pour un ProgID, la version par défaut est 1. Si vous ne spécifiez pas *nom1. nom2*, le nom par défaut est *className. ClassName*. Si vous ne spécifiez pas `progid` et que vous spécifiez `vi_progid` , *nom1. nom2* est pris de `vi_progid` et la version (numéro séquentiel suivant) est ajoutée.

Si un bloc d’attributs qui utilise `progid` n’utilise pas non plus `uuid` , le compilateur vérifie le registre pour déterminer s' `uuid` il existe un pour le spécifié `progid` . Si `progid` n’est pas spécifié, la version (et le nom de la coclasse, si la création d’une coclasse) sera utilisée pour générer un `progid` .

`progid`implique l' `coclass` attribut, autrement dit, si vous spécifiez `progid` , il s’agit de la même chose que la spécification des `coclass` `progid` attributs et.

L' `progid` attribut entraîne l’inscription automatique d’une classe sous le nom spécifié. Le fichier. idl généré n’affiche pas la `progid` valeur.

Lorsque cet attribut est utilisé dans un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement ci-dessus, les informations spécifiées avec cet attribut sont utilisées dans la `GetProgID` fonction, injectées par l' `coclass` attribut. Pour plus d’informations, consultez l’attribut [coclass](coclass.md) .

## <a name="example"></a>Exemple

Consultez l’exemple de [coclass](coclass.md) pour obtenir un exemple d’utilisation de `progid` .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|`class`, `struct`|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Clé ProgID](/windows/win32/com/-progid--key)
