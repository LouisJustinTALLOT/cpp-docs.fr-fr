---
title: propputref (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: a9c4413e9bb8c7faa332bb842700dfcf84d6666a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166430"
---
# <a name="propputref"></a>propputref

Spécifie une fonction de définition de propriété qui utilise une référence au lieu d’une valeur.

## <a name="syntax"></a>Syntaxe

```cpp
[propputref]
```

## <a name="remarks"></a>Notes

L’attribut **PROPPUTREF** C++ a les mêmes fonctionnalités que l’attribut MIDL [PROPPUTREF](/windows/win32/Midl/propputref) .

## <a name="example"></a>Exemple

Consultez l’exemple de [Bindable](bindable.md) pour obtenir un exemple d’utilisation de **PROPPUTREF**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|`propget`, `propput`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)
