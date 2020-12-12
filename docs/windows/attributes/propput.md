---
description: 'En savoir plus sur : propput'
title: propput (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: f7b33996c4575de6b94fc3127c33a88c6f791aed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327384"
---
# <a name="propput"></a>propput

Spécifie une fonction de définition de propriété.

## <a name="syntax"></a>Syntaxe

```cpp
[propput]
```

## <a name="remarks"></a>Notes

L’attribut C++ **propput** a les mêmes fonctionnalités que l’attribut MIDL [propput](/windows/win32/Midl/propput) .

## <a name="example"></a>Exemple

Consultez l’exemple de [liaison](bindable.md) pour obtenir un exemple d’utilisation de **propput**.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|`propget`, `propputref`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)
