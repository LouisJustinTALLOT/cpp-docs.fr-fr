---
title: Erreur du compilateur C2790 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2790
dev_langs:
- C++
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc2c6b238fab7e42c0754e613b62756a86a5bb31
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069571"
---
# <a name="compiler-error-c2790"></a>Erreur du compilateur C2790

'super' : ce mot clé peut uniquement être utilisé dans le corps de fonction membre de classe

Ce message d’erreur apparaît si l’utilisateur tente utilise le mot clé [super](../../cpp/super.md) en dehors du contexte d’une fonction membre.

L’exemple suivant génère l’erreur C2790 :

```
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```