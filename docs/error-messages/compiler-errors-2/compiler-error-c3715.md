---
title: Erreur du compilateur C3715 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63ae3486b4db21a3aa241d5ebdbbfa0cdc6806f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026554"
---
# <a name="compiler-error-c3715"></a>Erreur du compilateur C3715

'pointeur' : doit être un pointeur vers 'class'

Vous avez spécifié un pointeur dans [__hook](../../cpp/hook.md) ou [__unhook](../../cpp/unhook.md) qui ne pointe pas vers une classe valide. Pour corriger cette erreur, vérifiez que votre `__hook` et `__unhook` appels spécifient des pointeurs vers des classes valides.