---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4544'
title: Avertissement du compilateur (niveau 1) C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: cd7d4dddd43a8cac0ce4eb5115dbbadad3d56103
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294754"
---
# <a name="compiler-warning-level-1-c4544"></a>Avertissement du compilateur (niveau 1) C4544

'déclaration' : argument template par défaut ignoré sur cette déclaration de modèle

Un argument template par défaut a été spécifié dans un emplacement incorrect et a été ignoré. Un argument template par défaut pour un modèle de classe peut uniquement être spécifié dans la déclaration ou la définition du modèle de classe et non sur un membre du modèle de classe.

Cet exemple génère l'erreur C4545 et l'exemple suivant montre comment résoudre le problème :

```cpp
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

Dans cet exemple, le paramètre par défaut s'applique au modèle de classe `S` :

```cpp
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```
