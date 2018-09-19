---
title: Erreur du compilateur C2070 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2070
dev_langs:
- C++
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23daf8a8c25e132aa0717715a742352537010c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044078"
---
# <a name="compiler-error-c2070"></a>Erreur du compilateur C2070

'type' : opérande sizeof non conforme

Le [sizeof](../../cpp/sizeof-operator.md) opérateur exige un nom d’expression ou de type.

L’exemple suivant génère l’erreur C2070 :

```
// C2070.cpp
void func() {}
int main() {
   int a;
   a = sizeof(func);   // C2070
}
```

Solution possible :

```
// C2070b.cpp
void func() {}
int main() {
   int a;
   a = sizeof(a);
}
```