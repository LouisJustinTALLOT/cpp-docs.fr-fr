---
description: 'En savoir plus sur : erreur du compilateur C2427'
title: Erreur du compilateur C2427
ms.date: 11/04/2016
f1_keywords:
- C2427
helpviewer_keywords:
- C2427
ms.assetid: a7d421af-6180-40b4-b7a6-9f3bc7dfaaf9
ms.openlocfilehash: ae1131eb511d9d3f1affad56b576cebd19cb5213
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190170"
---
# <a name="compiler-error-c2427"></a>Erreur du compilateur C2427

'class' : impossible de définir une classe dans cette portée

Une tentative a été effectuée pour définir une classe imbriquée, mais la classe imbriquée est un membre d’une classe de base, et non de la classe la plus conteneur.

L’exemple suivant génère l’C2427 :

```cpp
// C2427.cpp
// compile with: /c
template <class T>
struct S {
   struct Inner;
};

struct Y : S<int> {};

struct Y::Inner {};   // C2427

// OK
template<typename T>
struct S<T>::Inner {};
```
