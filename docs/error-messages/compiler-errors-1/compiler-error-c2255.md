---
description: 'En savoir plus sur : erreur du compilateur C2255'
title: Erreur du compilateur C2255
ms.date: 11/04/2016
f1_keywords:
- C2255
helpviewer_keywords:
- C2255
ms.assetid: 67dc4cb0-de6b-4405-bd64-d47736367a93
ms.openlocfilehash: 9c7898ede43c9c25175854faeab5ee279a9c5635
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333853"
---
# <a name="compiler-error-c2255"></a>Erreur du compilateur C2255

'element' : non autorisé en dehors d’une définition de classe

Par exemple, une fonction non membre est déclarée **`friend`** .

L’exemple suivant génère l’erreur C2255 :

```cpp
// C2255.cpp
// compile with: /c
class A {
private:
   void func1();
   friend void func2();
};

friend void func1() {}   // C2255
void func2(){}
```
