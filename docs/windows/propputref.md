---
title: propputref | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2afa793371f2e9840bbb98efc9f745ecbdd29b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389328"
---
# <a name="propputref"></a>propputref

Spécifie une fonction de définition de propriété qui utilise une référence plutôt qu’une valeur.

## <a name="syntax"></a>Syntaxe

```cpp
[propputref]
```

## <a name="remarks"></a>Notes

Le **propputref** attribut C++ a les mêmes fonctionnalités que le [propputref](/windows/desktop/Midl/propputref) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](../windows/bindable.md) pour un exemple d’utilisation de **propputref**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|`propget`, `propput`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs de méthode](../windows/method-attributes.md)<br/>
[propget](../windows/propget.md)<br/>
[propput](../windows/propput.md)  