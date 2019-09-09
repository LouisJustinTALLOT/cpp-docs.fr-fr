---
title: vi_progid (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: fbf5ab2bc4263356a1cfcf789865a3f7e286ccd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514869"
---
# <a name="vi_progid"></a>vi_progid

Spécifie une forme indépendante de la version du ProgID.

## <a name="syntax"></a>Syntaxe

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Paramètres

*name*<br/>
ProgID indépendant de la version représentant l’objet.

Les ProgID présentent une version explicite de l’identificateur de classe (CLSID) utilisé pour identifier les objets COM/ActiveX.

## <a name="remarks"></a>Notes

L’attribut **vi_progid** C++ vous permet de spécifier un ProgID indépendant de la version pour un objet com. Un ProgID se présente sous la forme *nom1. nom2. version*. Un ProgID indépendant de la version n’a pas de *version*. Il est possible de spécifier à la `progid` fois les attributs et **vi_progid** sur `coclass`un. Si vous ne spécifiez pas **vi_progid**, le ProgID indépendant de la version est la valeur spécifiée par l’attribut [ProgID](progid.md) .

**vi_progid** implique l' `coclass` attribut, autrement dit, si vous spécifiez **vi_progid**, il s’agit de la même chose `coclass` que la spécification des attributs et **vi_progid** .

L’attribut **vi_progid** provoque l’inscription automatique d’une classe sous le nom spécifié. Le fichier. idl généré n’affiche pas la valeur ProgID.

Dans les projets ATL, si l’attribut [coclass](coclass.md) est également présent, le ProgID spécifié est utilisé par `GetVersionIndependentProgID` la fonction (insérée `coclass` par l’attribut).

## <a name="example"></a>Exemple

Consultez l’exemple [coclass](coclass.md) pour obtenir un exemple d’utilisation de **vi_progid**.

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
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Clé ProgID](/windows/win32/com/-progid--key)
