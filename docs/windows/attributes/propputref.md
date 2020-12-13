---
description: 'En savoir plus sur : propputref'
title: propputref (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: 5f09d742ef0df75df03e4f4d740181cfcaaa8f2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329669"
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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|`propget`, `propput`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)
