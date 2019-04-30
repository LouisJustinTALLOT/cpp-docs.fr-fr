---
title: Erreur du compilateur C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7eb0c00f4f4c5c59766bf305acfef89e12a6cfb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402773"
---
# <a name="compiler-error-c3200"></a>Erreur du compilateur C3200

'template' : argument template non valide pour le paramètre de modèle 'paramètre', de modèle de classe attendu

Vous avez passé un argument non valide à un modèle de classe. Le modèle de classe attend un modèle en tant que paramètre. Dans l’exemple suivant, l’appel `Y<int, int> aY` génère l’erreur C3200. Le premier paramètre doit être un modèle, tel que `Y<X, int> aY`.

```
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