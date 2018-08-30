---
title: propput | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propput
dev_langs:
- C++
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f6adf0f2eaf61c3a280c8ca248cffea2f05bda6f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213167"
---
# <a name="propput"></a>propput

Spécifie une fonction de définition de propriété.

## <a name="syntax"></a>Syntaxe

```cpp
[propput]
```

## <a name="remarks"></a>Notes

Le **propput** attribut C++ a les mêmes fonctionnalités que le [propput](/windows/desktop/Midl/propput) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](../windows/bindable.md) pour un exemple d’utilisation de **propput**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|`propget`, `propputref`|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs de méthode](../windows/method-attributes.md)  
[propget](../windows/propget.md)  
[propputref](../windows/propputref.md)