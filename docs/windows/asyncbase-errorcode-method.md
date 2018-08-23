---
title: Asyncbase::ErrorCode, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7336824d04745440a1f6152ebacfed2afc62258e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602376"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode, méthode

Récupère le code d’erreur pour l’opération asynchrone actuelle.

## <a name="syntax"></a>Syntaxe

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Paramètres

*Erreur*  
L’emplacement où cette opération stocke le code d’erreur actuel.

## <a name="remarks"></a>Notes

Cette opération est thread-safe.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)