---
description: 'En savoir plus sur : erreur du compilateur C2589'
title: Erreur du compilateur C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: b874988f65ef41a9cde19e4c0229a6cb54859b28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177495"
---
# <a name="compiler-error-c2589"></a>Erreur du compilateur C2589

'identificateur' : jeton non conforme à droite de' :: '

Si un nom de classe, de structure ou d’Union apparaît à gauche de l’opérateur de résolution de portée (deux-points), le jeton à droite doit être un membre de classe, de structure ou d’Union. Dans le cas contraire, tous les identificateurs globaux peuvent apparaître à droite.

L’opérateur de résolution de portée ne peut pas être surchargé.

L’exemple suivant génère l’C2589 :

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
