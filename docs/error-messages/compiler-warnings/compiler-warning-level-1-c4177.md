---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4177'
title: Avertissement du compilateur (niveau 1) C4177
ms.date: 11/04/2016
f1_keywords:
- C4177
helpviewer_keywords:
- C4177
ms.assetid: 2b05a5b3-696e-4f21-818e-227b9335e748
ms.openlocfilehash: 0febb9f44f817932221cb6f633807cbfcc9b349e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266830"
---
# <a name="compiler-warning-level-1-c4177"></a>Avertissement du compilateur (niveau 1) C4177

\#le pragma pragma doit être au niveau de la portée globale

Le pragma [pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) ne doit pas être utilisé dans une portée locale. Le **pragma** n’est pas valide si une portée globale est rencontrée après la portée actuelle.

L’exemple suivant génère l’avertissement C4177 :

```cpp
// C4177.cpp
// compile with: /W1
// #pragma bss_seg("global")   // OK

int main() {
   #pragma bss_seg("local")    // C4177
}
```
