---
title: propputref (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: dbb5d5966fc82f69be0ed7d2fa0a66ad558a7915
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839905"
---
# <a name="propputref"></a>propputref

Spécifie une fonction de définition de propriété qui utilise une référence au lieu d’une valeur.

## <a name="syntax"></a>Syntaxe

```cpp
[propputref]
```

## <a name="remarks"></a>Notes

L’attribut C++ **PROPPUTREF** a les mêmes fonctionnalités que l’attribut MIDL [PROPPUTREF](/windows/win32/Midl/propputref) .

## <a name="example"></a>Exemple

Consultez l’exemple de [Bindable](bindable.md) pour obtenir un exemple d’utilisation de **PROPPUTREF**.

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|`propget`, `propput`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)
