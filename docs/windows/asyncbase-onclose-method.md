---
title: Asyncbase::OnClose, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnClose
dev_langs:
- C++
helpviewer_keywords:
- OnClose method
ms.assetid: 96766450-c262-4611-8534-7d190b799142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 866e4a285a92fb7d80d0fe0d8240ebdda107de23
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419388"
---
# <a name="asyncbaseonclose-method"></a>AsyncBase::OnClose, méthode

En cas de substitution dans une classe dérivée, ferme une opération asynchrone.

## <a name="syntax"></a>Syntaxe

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)<br/>
[AsyncBase::Close, méthode](../windows/asyncbase-close-method.md)