---
description: 'En savoir plus sur : erreur du compilateur C2688'
title: Erreur du compilateur C2688
ms.date: 11/04/2016
f1_keywords:
- C2688
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
ms.openlocfilehash: 17219fe6f4358b73ace0435e60d8fc2b7a9b6df8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330683"
---
# <a name="compiler-error-c2688"></a>Erreur du compilateur C2688

'C2 :: fgrv' : retours covariants avec un héritage virtuel ou multiple non pris en charge pour les fonctions varargs

Les types de retour covariants ne sont pas pris en charge dans Visual C++ lorsqu’une fonction contient des arguments de variables.

Pour résoudre cette erreur, définissez vos fonctions de manière à ce qu’elles n’utilisent pas d’arguments de variables, ou transmettez les valeurs de retour de la même manière pour toutes les fonctions virtuelles.

L’exemple suivant génère l’C2688 :

```cpp
// C2688.cpp
struct G1 {};
struct G2 {};
struct G3 : G1, G2 {};
struct G4 {};
struct G5 {};
struct G6 : G4, G5 {};
struct G7 : G3, G6 {};

struct C1 {
   virtual G4& fgrv(int,...);
};

struct C2 : C1 {
   virtual G7& fgrv(int,...);   // C2688, does not return G4&
};
```
