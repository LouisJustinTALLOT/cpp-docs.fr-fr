---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4549'
title: Avertissement du compilateur (niveau 1) C4549
ms.date: 11/04/2016
f1_keywords:
- C4549
helpviewer_keywords:
- C4549
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
ms.openlocfilehash: 4f6da48b0c1592ed706c33336ec0bcd13108591b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265985"
---
# <a name="compiler-warning-level-1-c4549"></a>Avertissement du compilateur (niveau 1) C4549

'opérateur' : l’opérateur avant la virgule n’a aucun effet ; souhaitiez-vous’operator' ?

Le compilateur a détecté une expression de virgule mal formée.

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

L’exemple suivant génère l’C4549 :

```cpp
// C4549.cpp
// compile with: /W1
#pragma warning (default : 4549)

int main() {
   int i = 0, k = 0;

   if ( i == 0, k )   // C4549
   // try the following line instead
   // if ( i == 0 )
      i++;
}
```
