---
description: 'En savoir plus sur : erreur du compilateur C2908'
title: Erreur du compilateur C2908
ms.date: 11/04/2016
f1_keywords:
- C2908
helpviewer_keywords:
- C2908
ms.assetid: 49cd2a21-cad8-4ba0-9a0b-3a0190d9344c
ms.openlocfilehash: 086bc8d20f40f8dabb1aff1e30b45a73de8ab16a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270652"
---
# <a name="compiler-error-c2908"></a>Erreur du compilateur C2908

spécialisation explicite ; 'template’a déjà été instancié

Une spécialisation du modèle principal se produit avant la spécialisation explicite.

L’exemple suivant génère l’C2908 :

```cpp
// C2908.cpp
// compile with: /c
template<class T> class X {};

void f() {
X<int> x;   //specialization and instantiation
            //of X<int>
}

template<> class X<int> {}  // C2908, explicit specialization
```
