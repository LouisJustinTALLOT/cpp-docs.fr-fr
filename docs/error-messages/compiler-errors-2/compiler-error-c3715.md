---
description: 'En savoir plus sur : erreur du compilateur C3715'
title: Erreur du compilateur C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: b64f7039b15363b36f6cc761f834c64dae255f76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189455"
---
# <a name="compiler-error-c3715"></a>Erreur du compilateur C3715

'pointeur' : doit être un pointeur vers’class'

Vous avez spécifié un pointeur dans [`__hook`](../../cpp/hook.md) ou [`__unhook`](../../cpp/unhook.md) qui ne pointe pas vers une classe valide. Pour corriger cette erreur, assurez-vous que vos **`__hook`** **`__unhook`** appels et spécifient des pointeurs vers des classes valides.
