---
title: Erreur du compilateur C2381 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f09cd8c16eeb5ec797643cb6653d069df41b136
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076942"
---
# <a name="compiler-error-c2381"></a>Erreur du compilateur C2381

'fonction' : redéfinition ; __declspec (noreturn) est différent

Une fonction a été déclarée et puis définie mais la définition utilisée la [noreturn](../../cpp/noreturn.md) `__declspec` modificateur. L’utilisation de `noreturn` constitue une redéfinition de la fonction ; la déclaration et la définition doivent s’accorder sur l’utilisation de `noreturn`.

L’exemple suivant génère l’erreur C2381 :

```
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```