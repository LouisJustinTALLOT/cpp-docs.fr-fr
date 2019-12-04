---
title: Erreur du compilateur C3201
ms.date: 11/04/2016
f1_keywords:
- C3201
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
ms.openlocfilehash: 4da6616c59ea4b8a720c8e2dc9742e37a9939171
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738763"
---
# <a name="compiler-error-c3201"></a>Erreur du compilateur C3201

la liste des paramètres de modèle pour la classe de modèle 'modèle' ne correspond pas à celle du paramètre de modèle 'modèle'

Vous avez passé un modèle de classe dans l’argument à un modèle de classe qui n’accepte pas de paramètre de modèle, ou vous avez passé un nombre inapproprié d’arguments de modèle pour l’argument de modèle par défaut.

```cpp
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
