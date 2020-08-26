---
title: propget (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 2627213d1d1dc74edb33d70ac45f3b7bbd38ba6b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839970"
---
# <a name="propget"></a>propget

Spécifie une fonction d’accesseur de propriété.

## <a name="syntax"></a>Syntaxe

```cpp
[propget]
```

## <a name="remarks"></a>Notes

L’attribut C++ **propget** a les mêmes fonctionnalités que l’attribut MIDL [propget](/windows/win32/Midl/propget) .

## <a name="example"></a>Exemple

Consultez l’exemple de [liaison](bindable.md) pour obtenir un exemple d’utilisation de **propget**.

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|`propput`, `propputref`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)
