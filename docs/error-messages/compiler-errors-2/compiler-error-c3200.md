---
description: 'En savoir plus sur : erreur du compilateur C3200'
title: Erreur du compilateur C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: c693878628ff0bd9dddcb2f100ca652910b0fb89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330662"
---
# <a name="compiler-error-c3200"></a>Erreur du compilateur C3200

'modèle' : argument template non valide pour le paramètre de modèle’paramètre', modèle de classe ATTENDU

Vous avez passé un argument non valide à un modèle de classe. Le modèle de classe attend un modèle en tant que paramètre. Dans l’exemple suivant, l’appel de `Y<int, int> aY` génère la commande C3200. Le premier paramètre doit être un modèle, tel que `Y<X, int> aY` .

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
