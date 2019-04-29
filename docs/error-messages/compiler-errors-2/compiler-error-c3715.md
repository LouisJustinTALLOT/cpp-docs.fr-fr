---
title: Erreur du compilateur C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 94a451bbe936507ac3b33747065a9b6aac9edd02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328326"
---
# <a name="compiler-error-c3715"></a>Erreur du compilateur C3715

'pointeur' : doit être un pointeur vers 'class'

Vous avez spécifié un pointeur dans [__hook](../../cpp/hook.md) ou [__unhook](../../cpp/unhook.md) qui ne pointe pas vers une classe valide. Pour corriger cette erreur, vérifiez que votre `__hook` et `__unhook` appels spécifient des pointeurs vers des classes valides.