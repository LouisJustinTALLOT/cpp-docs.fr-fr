---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4547'
title: Avertissement du compilateur (niveau 1) C4547
ms.date: 11/04/2016
f1_keywords:
- C4547
helpviewer_keywords:
- C4547
ms.assetid: 3edf1c2e-c0d5-444d-ae83-44a7cce24bb2
ms.openlocfilehash: 59295f7f8a0a71e638a28ddc3a316e9c020cc652
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266011"
---
# <a name="compiler-warning-level-1-c4547"></a>Avertissement du compilateur (niveau 1) C4547

'opérateur' : l’opérateur avant la virgule n’a aucun effet ; opérateur avec effet secondaire ATTENDU

Le compilateur a détecté une expression de virgule mal formée.

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

L’exemple suivant génère l’C4547 :

```cpp
// C4547.cpp
// compile with: /W1
#pragma warning (default : 4547)
int i = 0;
int j = 1;
int main() {
   int l = (i != i,0);   // C4547
   // try the following line instead
   // int l = (i != i);
   // or
   // int l = ((void)(i != i),0);
}
```
