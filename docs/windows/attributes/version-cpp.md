---
title: version (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: b537f56c39c33abc52897cf53ea2cc0fb24ee458
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213799"
---
# <a name="version-c"></a>version (C++)

Identifie une version particulière parmi plusieurs versions d’une classe.

## <a name="syntax"></a>Syntaxe

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Paramètres

*version*<br/>
Numéro de version du `coclass`. S’il n’est pas spécifié, 1,0 sera placé dans le fichier. idl.

## <a name="remarks"></a>Notes

L’attribut de **version** C++ a les mêmes fonctionnalités que l’attribut MIDL de la [version](/windows/win32/Midl/version) et est passé au fichier. idl généré.

## <a name="example"></a>Exemple

Consultez l’exemple [pouvant être lié](bindable.md) pour obtenir un exemple d’utilisation de la **version**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Repeatable Read**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
