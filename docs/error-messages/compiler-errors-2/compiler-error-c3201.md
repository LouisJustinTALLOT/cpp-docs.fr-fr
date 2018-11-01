---
title: Erreur du compilateur C3201
ms.date: 11/04/2016
f1_keywords:
- C3201
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
ms.openlocfilehash: 92e068103563f7427de7b394536e72b06fab3374
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504544"
---
# <a name="compiler-error-c3201"></a>Erreur du compilateur C3201

la liste des paramètres de modèle pour la classe de modèle 'modèle' ne correspond pas à celle du paramètre de modèle 'modèle'

Vous avez passé un modèle de classe dans l’argument à un modèle de classe qui n’accepte pas de paramètre de modèle, ou vous avez passé un nombre inapproprié d’arguments de modèle pour l’argument de modèle par défaut.

```
// C3201.cpp
template<typename T1, typename T2>
class X1
{
};

template<template<typename T> class U = X1>   // C3201
class X2
{
};

template<template<typename T, typename V> class U = X1>   // OK
class X3
{
};
```