---
description: 'En savoir plus sur : erreur du compilateur C2823'
title: Erreur du compilateur C2823
ms.date: 11/04/2016
f1_keywords:
- C2823
helpviewer_keywords:
- C2823
ms.assetid: 982b1b35-1a7c-456e-b711-f80cfe2d571e
ms.openlocfilehash: 57dacaf144f23a1e8486d6a2849fffce0ff8be52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194668"
---
# <a name="compiler-error-c2823"></a>Erreur du compilateur C2823

> modèle typedef non conforme

Les modèles ne sont pas autorisés dans les **`typedef`** définitions.

## <a name="example"></a>Exemple

L’exemple suivant génère C2823 et montre une façon de le corriger :

```cpp
// C2823.cpp
template<class T>
typedef struct x {
   T i;   // C2823 can't use T, specify data type and delete template
   int i;   // OK
} x1;
```
