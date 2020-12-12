---
description: 'En savoir plus sur : erreur du compilateur C2897'
title: Erreur du compilateur C2897
ms.date: 11/04/2016
f1_keywords:
- C2897
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
ms.openlocfilehash: b1a1f66987aa4bbd01fdf12f88f8933e3436938a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270873"
---
# <a name="compiler-error-c2897"></a>Erreur du compilateur C2897

un destructeur/finaliseur ne peut pas être un modèle de fonction

Les destructeurs et finaliseurs ne peuvent pas être surchargés, donc la déclaration d’un destructeur en tant que modèle (qui définit un ensemble de destructeurs) n’est pas autorisée.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2897.

```cpp
// C2897.cpp
// compile with: /c
class X {
public:
   template<typename T> ~X() {}   // C2897
};
```

L’exemple suivant génère l’C2897.

```cpp
// C2897_b.cpp
// compile with: /c /clr
ref struct R2 {
protected:
   template<typename T> !R2(){}   // C2897 error
};
```
