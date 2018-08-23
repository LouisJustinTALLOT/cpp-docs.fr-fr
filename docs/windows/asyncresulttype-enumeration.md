---
title: Asyncresulttype, énumération | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
dev_langs:
- C++
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a79ef02302208aa14bc1620e486fcfbc6e12253
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591261"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType (énumération)

Spécifie le type de résultat retourné par la `GetResults()` (méthode).

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`MultipleResults`|Un ensemble de résultats multiples, qui sont présentées progressivement entre `Start` état et avant `Close()` est appelée.|
|`SingleResult`|Un résultat unique, qui est présenté après la `Complete` événement se produit.|

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)