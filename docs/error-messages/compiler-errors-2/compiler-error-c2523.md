---
title: Erreur du compilateur C2523
ms.date: 11/04/2016
f1_keywords:
- C2523
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
ms.openlocfilehash: 56b0f88949d7a7fa5af945ab5d03ee9a480d6d3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746420"
---
# <a name="compiler-error-c2523"></a>Erreur du compilateur C2523

'Class :: ~ identifier' : incompatibilité de la balise de destructeur/finaliseur

Le nom du destructeur doit être le nom de la classe précédé d’un tilde (`~`). Le constructeur et le destructeur sont les seuls membres qui ont le même nom que la classe.

L’exemple suivant génère l’C2523 :

```cpp
// C2523.cpp
// compile with: /c
class A {
   ~B();    // C2523
   ~A();   // OK
};
```
