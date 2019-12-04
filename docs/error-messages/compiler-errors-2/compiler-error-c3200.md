---
title: Erreur du compilateur C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7f6b514231bcda18404e891e0acbe457c8f95146
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738776"
---
# <a name="compiler-error-c3200"></a>Erreur du compilateur C3200

'modèle' : argument template non valide pour le paramètre de modèle’paramètre', modèle de classe ATTENDU

Vous avez passé un argument non valide à un modèle de classe. Le modèle de classe attend un modèle en tant que paramètre. Dans l’exemple suivant, l’appel de `Y<int, int> aY` génère la commande C3200. Le premier paramètre doit être un modèle, tel que `Y<X, int> aY`.

```cpp
// C3200.cpp
template<typename T>
class X
{
};

template<template<typename U> class T1, typename T2>
class Y
{
};

int main()
{
   Y<int, int> y;   // C3200
}
```
