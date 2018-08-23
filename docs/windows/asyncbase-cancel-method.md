---
title: Asyncbase::Cancel, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbf216d672dd22e453f8c213f7a9f34f08a47273
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593135"
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel, méthode

Annule une opération asynchrone.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   Cancel
)(void);
```

## <a name="return-value"></a>Valeur de retour

Par défaut, retourne toujours S_OK.

## <a name="remarks"></a>Notes

**Cancel()** est une implémentation par défaut de `IAsyncInfo::Cancel`, et n’effectue aucun travail réel. Pour réellement annuler une opération asynchrone, remplacer le `OnCancel()` méthode virtuelle pure.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)