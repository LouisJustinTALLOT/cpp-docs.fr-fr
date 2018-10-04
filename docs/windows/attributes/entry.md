---
title: entrée (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 95eb37898d4934740e1520df758ed33d3dd4c79a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790657"
---
# <a name="entry"></a>entry

Spécifie une fonction exportée ou une constante dans un module en identifiant le point d’entrée dans la DLL.

## <a name="syntax"></a>Syntaxe

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
L’ID du point d’entrée.

## <a name="remarks"></a>Notes

Le **entrée** attribut C++ a les mêmes fonctionnalités que le [entrée](/windows/desktop/Midl/entry) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [idl_module](idl-module.md) pour un exemple d’utilisation de **entrée**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Attribut `idl_module`|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)  