---
title: Erreur du compilateur C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: b29f7dac6c6d71e12eb0f003cdfc151dd2c349a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347897"
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