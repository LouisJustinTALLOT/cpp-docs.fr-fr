---
title: oleautomation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.oleautomation
dev_langs:
- C++
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e321f8039cbb51dda8cc9103601bd91218f1cdab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419430"
---
# <a name="oleautomation"></a>oleautomation

Indique qu’une interface est compatible avec Automation.

## <a name="syntax"></a>Syntaxe

```cpp
[oleautomation]
```

## <a name="remarks"></a>Notes

Le **oleautomation** attribut C++ a les mêmes fonctionnalités que le [oleautomation](/windows/desktop/Midl/oleautomation) attribut MIDL.

## <a name="example"></a>Exemple

Reportez-vous aux exemples de [defaultvalue](../windows/defaultvalue.md) et [nonextensible](../windows/nonextensible.md) pour un exemple d’utilisation de **oleautomation**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|**dispinterface**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs d’interface](../windows/interface-attributes.md)  