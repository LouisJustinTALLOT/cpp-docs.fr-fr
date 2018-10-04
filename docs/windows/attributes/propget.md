---
title: propget (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propget
dev_langs:
- C++
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44a5b06a4d94bc431d33fa29cdcef4738e43ca54
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790921"
---
# <a name="propget"></a>propget

Spécifie une fonction d’accesseur de propriété.

## <a name="syntax"></a>Syntaxe

```cpp
[propget]
```

## <a name="remarks"></a>Notes

Le **propget** attribut C++ a les mêmes fonctionnalités que le [propget](/windows/desktop/Midl/propget) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](bindable.md) pour un exemple d’utilisation de **propget**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|`propput`, `propputref`|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)  