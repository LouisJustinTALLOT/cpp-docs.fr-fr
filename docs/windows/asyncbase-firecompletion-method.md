---
title: Asyncbase::firecompletion, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs:
- C++
helpviewer_keywords:
- FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19b796b1fbc618bb909b186aa86d3c893c8536c5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600254"
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion, méthode

Appelle le Gestionnaire d’événements de saisie semi-automatique, ou réinitialise le délégué de progression interne.

## <a name="syntax"></a>Syntaxe

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

## <a name="remarks"></a>Notes

La première version de **FireCompletion()** réinitialise la variable de délégué de progression interne. La deuxième version appelle le Gestionnaire d’événements de saisie semi-automatique si l’opération asynchrone est terminée.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)