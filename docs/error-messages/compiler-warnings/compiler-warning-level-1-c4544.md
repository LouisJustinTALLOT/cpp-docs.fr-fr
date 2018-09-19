---
title: Compilateur avertissement (niveau 1) C4544 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4544
dev_langs:
- C++
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7cd274f0d1b595d374e1b108db40a51395b968
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084274"
---
# <a name="compiler-warning-level-1-c4544"></a>Avertissement du compilateur (niveau 1) C4544

’déclaration’ : argument template par défaut ignoré sur cette déclaration de modèle

Un argument template par défaut a été spécifié dans un emplacement incorrect et a été ignoré. Un argument template par défaut pour un modèle de classe peut uniquement être spécifié dans la déclaration ou la définition du modèle de classe et non sur un membre du modèle de classe.

Cet exemple génère l'erreur C4545 et l'exemple suivant montre comment résoudre le problème :

```
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

```
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