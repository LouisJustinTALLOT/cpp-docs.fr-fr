---
description: 'En savoir plus sur : erreur du compilateur C2502'
title: Erreur du compilateur C2502
ms.date: 11/04/2016
f1_keywords:
- C2502
helpviewer_keywords:
- C2502
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
ms.openlocfilehash: 6ee501a5fa3601ef5e4b97d4be5a8e59463ce797
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275930"
---
# <a name="compiler-error-c2502"></a>Erreur du compilateur C2502

'identificateur' : modificateurs d’accès trop nombreux sur la classe de base

La classe de base a plusieurs modificateurs d’accès. Un seul modificateur d’accès ( **`public`** , **`private`** ou **`protected`** ) est autorisé.

L’exemple suivant génère l’C2502 :

```cpp
// C2502.cpp
// compile with: /c
class A { };
class B { };
class C : private public A { };   // C2502

// OK
class D : private A {};
class E : public A, private B {};
```
