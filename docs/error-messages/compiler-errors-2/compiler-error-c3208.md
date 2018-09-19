---
title: Erreur du compilateur C3208 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3208
dev_langs:
- C++
helpviewer_keywords:
- C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53564517eaed44c21e6eccb58ad6399788129687
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078502"
---
# <a name="compiler-error-c3208"></a>Erreur du compilateur C3208

'function' : la liste de paramètres template pour le modèle de classe 'class' ne correspond pas à la liste de paramètres de modèle pour le paramètre template du modèle 'parameter'

Un paramètre template de modèle n’a pas le même nombre de paramètres template que le modèle de classe fourni.

L’exemple suivant génère l’erreur C3208 :

```
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