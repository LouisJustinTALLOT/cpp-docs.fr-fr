---
title: Erreur du compilateur C2724
ms.date: 11/04/2016
f1_keywords:
- C2724
helpviewer_keywords:
- C2724
ms.assetid: 4e4664bc-8c96-4156-b79f-03436f532ea8
ms.openlocfilehash: f48bf45eeed491469b161ac1edcdb57d04eb5863
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760684"
---
# <a name="compiler-error-c2724"></a>Erreur du compilateur C2724

'identifier' : 'static’ne doit pas être utilisé sur les fonctions membres définies au niveau de la portée du fichier

Les fonctions membres statiques doivent être déclarées avec une liaison externe.

L’exemple suivant génère l’C2724 :

```cpp
// C2724.cpp
class C {
   static void func();
};

static void C::func(){};   // C2724
// try the following line instead
// void C::func(){};
```
