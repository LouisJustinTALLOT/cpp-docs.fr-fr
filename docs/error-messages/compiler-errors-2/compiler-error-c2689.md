---
description: 'En savoir plus sur : erreur du compilateur C2689'
title: Erreur du compilateur C2689
ms.date: 11/04/2016
f1_keywords:
- C2689
helpviewer_keywords:
- C2689
ms.assetid: b5216fba-524d-4194-9168-26e9dc5210ce
ms.openlocfilehash: 532db26a3c0da3191c9b15215d470618e561e76a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326712"
---
# <a name="compiler-error-c2689"></a>Erreur du compilateur C2689

'fonction' : une fonction friend ne peut pas être définie dans une classe locale

Vous pouvez déclarer, mais pas définir une fonction friend dans une classe locale.

L’exemple suivant génère l’C2689 :

```cpp
// C2689.cpp
// compile with: /c
void g() {
   void f2();
   class X {
      friend void f2(){}   // C2689
      friend void f2();   // OK
   };
}
```
