---
title: Erreur du compilateur C3715 | Documents Microsoft
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
ms.openlocfilehash: 9412592ac177fb49f065975db469c9f77b98e8c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265894"
---
# <a name="compiler-error-c3715"></a>Erreur du compilateur C3715
'pointeur' : doit être un pointeur vers 'class'  
  
 Vous avez spécifié un pointeur dans [__hook](../../cpp/hook.md) ou [__unhook](../../cpp/unhook.md) qui ne pointe pas vers une classe valide. Pour corriger cette erreur, assurez-vous que votre `__hook` et `__unhook` appels spécifient des pointeurs vers des classes valides.