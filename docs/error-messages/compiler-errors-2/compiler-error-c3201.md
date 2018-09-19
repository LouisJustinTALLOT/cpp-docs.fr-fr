---
title: Erreur du compilateur C3201 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3201
dev_langs:
- C++
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 466899de89e1f8760ec78e7d346ef949fab667be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074251"
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