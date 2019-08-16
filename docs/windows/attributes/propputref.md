---
title: propputref (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: 9dc21494886f80890bcfde7f29bb3d6c86b4a51b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514181"
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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|`propget`, `propput`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)