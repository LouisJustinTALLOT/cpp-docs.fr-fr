---
description: 'En savoir plus sur : erreur du compilateur C2381'
title: Erreur du compilateur C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: ccaed8e5fc637ffb7e5cd2a33a00ddb5cf7c102b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282174"
---
# <a name="compiler-error-c2381"></a>Erreur du compilateur C2381

'fonction' : redéfinition ; __declspec (noreturn) est différent

Une fonction a été déclarée, puis définie, mais la [](../../cpp/noreturn.md) définition a utilisé le **`__declspec`** modificateur noreturn. L’utilisation de `noreturn` constitue une redéfinition de la fonction ; la déclaration et la définition doivent s’accorder sur l’utilisation de `noreturn` .

L’exemple suivant génère l’C2381 :

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
