---
title: version (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: 9a432267632b1f2a716a833a485b182cd93a27e2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514879"
---
# <a name="version-c"></a>version (C++)

Identifie une version particulière parmi plusieurs versions d’une classe.

## <a name="syntax"></a>Syntaxe

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Paramètres

*version*<br/>
Numéro de version de `coclass`. S’il n’est pas spécifié, 1,0 sera placé dans le fichier. idl.

## <a name="remarks"></a>Notes

L’attribut **version** C++ a les mêmes fonctionnalités que l’attribut MIDL de la [version](/windows/win32/Midl/version) et est passé au fichier. idl généré.

## <a name="example"></a>Exemple

Consultez l’exemple [pouvant être lié](bindable.md) pour obtenir un exemple d’utilisation de la **version**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs de classe](class-attributes.md)