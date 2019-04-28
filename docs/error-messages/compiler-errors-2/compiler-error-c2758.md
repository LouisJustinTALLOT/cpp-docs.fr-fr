---
title: Erreur du compilateur C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c3a86b8b8c7f122929a52221d4f01a17c50395be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257658"
---
# <a name="compiler-error-c2758"></a>Erreur du compilateur C2758

'membre' : un membre de type référence const doit être initialisé

L'erreur du compilateur C2758 survient quand le constructeur n'initialise pas un membre du type de référence dans une liste d'initialiseurs. Le compilateur laisse le membre non défini. Les variables du membre de référence doivent être initialisées quand elles sont déclarées ou se voir attribuer une valeur dans la liste d'initialisation du constructeur.

L'exemple suivant génère l'erreur C2758 :

```
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```