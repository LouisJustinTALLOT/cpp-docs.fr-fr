---
title: propget (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 044562ba870d6e36ddfcec0c7e84253b111a9eea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514209"
---
# <a name="propget"></a>propget

Spécifie une fonction d’accesseur de propriété.

## <a name="syntax"></a>Syntaxe

```cpp
[propget]
```

## <a name="remarks"></a>Notes

L’attribut **propget** C++ a les mêmes fonctionnalités que l’attribut MIDL [propget](/windows/win32/Midl/propget) .

## <a name="example"></a>Exemple

Consultez l’exemple de [liaison](bindable.md) pour obtenir un exemple d’utilisation de **propget**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|`propput`, `propputref`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)