---
description: 'En savoir plus sur : erreur du compilateur C2503'
title: Erreur du compilateur C2503
ms.date: 11/04/2016
f1_keywords:
- C2503
helpviewer_keywords:
- C2503
ms.assetid: da86cc89-fd04-400b-aa8d-a5ffaf7e3918
ms.openlocfilehash: 941af8af7fc4399e3c091b9d12a882619f4fc62c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213089"
---
# <a name="compiler-error-c2503"></a>Erreur du compilateur C2503

'classe' : les classes de base ne peuvent pas contenir de tableaux de taille zéro

Une classe ou une structure de base contient un tableau de taille zéro. Un tableau dans une classe doit avoir au moins un élément.

L’exemple suivant génère l’C2503 :

```cpp
// C2503.cpp
// compile with: /c
class A {
   public:
   int array [];
};

class B : A {};    // C2503

class C {
public:
   int array [10];
};

class D : C {};
```
