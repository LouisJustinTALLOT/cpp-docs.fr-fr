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
ms.openlocfilehash: 8da9da0ffbfb8291082f7f600ca72bf1937c3bfc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435543"
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

*Erreur*<br/>
L’emplacement où cette opération stocke le code d’erreur actuel.

## <a name="remarks"></a>Notes

Cette opération est thread-safe.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)