---
title: propput (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: 5e10edba60832112a9023f796be56d88afd52042
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514195"
---
# <a name="propput"></a>propput

Spécifie une fonction de définition de propriété.

## <a name="syntax"></a>Syntaxe

```cpp
[propput]
```

## <a name="remarks"></a>Notes

L’attribut **propput** C++ a les mêmes fonctionnalités que l’attribut MIDL [propput](/windows/win32/Midl/propput) .

## <a name="example"></a>Exemple

Consultez l’exemple de [liaison](bindable.md) pour obtenir un exemple d’utilisation de **propput**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|`propget`, `propputref`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)