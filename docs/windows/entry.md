---
title: entrée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a40ad39b089ea68209bfef2997f015c355ca6893
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414041"
---
# <a name="entry"></a>entry

Spécifie une fonction exportée ou une constante dans un module en identifiant le point d’entrée dans la DLL.

## <a name="syntax"></a>Syntaxe

```cpp
[ entry(
   id
) ]
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
L’ID du point d’entrée.

## <a name="remarks"></a>Notes

Le **entrée** attribut C++ a les mêmes fonctionnalités que le [entrée](/windows/desktop/Midl/entry) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [idl_module](../windows/idl-module.md) pour un exemple d’utilisation de **entrée**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Attribut `idl_module`|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  