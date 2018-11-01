---
title: Erreur du compilateur C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 94a451bbe936507ac3b33747065a9b6aac9edd02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660614"
---
# <a name="compiler-error-c3715"></a>Erreur du compilateur C3715

'pointeur' : doit être un pointeur vers 'class'

Vous avez spécifié un pointeur dans [__hook](../../cpp/hook.md) ou [__unhook](../../cpp/unhook.md) qui ne pointe pas vers une classe valide. Pour corriger cette erreur, vérifiez que votre `__hook` et `__unhook` appels spécifient des pointeurs vers des classes valides.