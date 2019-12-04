---
title: Erreur du compilateur C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: acb42f9b792b3908a153737bcec93a449b656147
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755445"
---
# <a name="compiler-error-c2577"></a>Erreur du compilateur C2577

'membre' : le destructeur/finaliseur ne peut pas avoir de type de retour

Un destructeur ou un finaliseur ne peut pas retourner une valeur de `void` ou d’un autre type. Supprimez l’instruction `return` de la définition du destructeur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2577.

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
