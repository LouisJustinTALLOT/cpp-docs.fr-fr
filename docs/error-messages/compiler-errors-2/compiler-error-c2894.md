---
title: Erreur du compilateur C2894
ms.date: 11/04/2016
f1_keywords:
- C2894
helpviewer_keywords:
- C2894
ms.assetid: 4e250579-2b59-4993-a6f4-49273e7ecf06
ms.openlocfilehash: 6909843539747b285a5390a66a7a323e4e9c5d00
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223458"
---
# <a name="compiler-error-c2894"></a>Erreur du compilateur C2894

les modèles ne peuvent pas être déclarés comme ayant une liaison’C'

Cette erreur peut être due à un modèle défini à l’intérieur d’un `extern "C"` bloc.

L’exemple suivant génère l’C2894 :

```cpp
// C2894.cpp
extern "C" {
   template<class T> class stack {};   // C2894 fail

   template<class T> void f(const T &aT) {}   // C2894
}
```

L’exemple suivant génère l’C2894 :

```cpp
// C2894b.cpp
// compile with: /c
extern "C" template<class T> void f(const T &aT) {}   // C2894

template<class T> void f2(const T &aT) {}   // OK
```
