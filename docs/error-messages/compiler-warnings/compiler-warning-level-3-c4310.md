---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4310'
title: Avertissement du compilateur (niveau 3) C4310
ms.date: 11/04/2016
f1_keywords:
- C4310
helpviewer_keywords:
- C4310
ms.assetid: cba3eca1-f1ed-499c-9243-337446bdbdd8
ms.openlocfilehash: 581d07005bd9932d4b0898a161a28b66e7d58b44
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344040"
---
# <a name="compiler-warning-level-3-c4310"></a>Avertissement du compilateur (niveau 3) C4310

Cast tronque la valeur constante

Une valeur de constante est convertie en un type plus petit. Le compilateur effectue le cast, qui tronque les données. L’exemple suivant génère l’C4310 :

```cpp
// C4310.cpp
// compile with: /W4
int main() {
   long int a;
   a = (char) 128;   // C4310, use value 0-127 to resolve
}
```
