---
description: 'En savoir plus sur : erreur du compilateur C3208'
title: Erreur du compilateur C3208
ms.date: 11/04/2016
f1_keywords:
- C3208
helpviewer_keywords:
- C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
ms.openlocfilehash: bd76a209fa3736449e8816473d0dee12daa93a61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173946"
---
# <a name="compiler-error-c3208"></a>Erreur du compilateur C3208

'function' : la liste de paramètres template pour le modèle de classe 'class' ne correspond pas à la liste de paramètres de modèle pour le paramètre template du modèle 'parameter'

Un paramètre template de modèle n’a pas le même nombre de paramètres template que le modèle de classe fourni.

L’exemple suivant génère l’erreur C3208 :

```cpp
// C3208.cpp
template <template <class T> class TT >
int f();

template <class T1, class T2>
struct S;

template <class T1>
struct R;

int i = f<S>();   // C3208
// try the following line instead
// int i = f<R>();
```
