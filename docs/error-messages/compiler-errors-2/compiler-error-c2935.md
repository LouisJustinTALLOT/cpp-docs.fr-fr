---
title: Erreur du compilateur C2935
ms.date: 11/04/2016
f1_keywords:
- C2935
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
ms.openlocfilehash: 676c238dfb0ae78dbe5b144b5242bfb4ccbda76c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756147"
---
# <a name="compiler-error-c2935"></a>Erreur du compilateur C2935

'classe' : type-class-id redéfini comme fonction globale

Vous ne pouvez pas utiliser une classe générique ou une classe de modèle comme fonction globale.

Cette erreur peut se produire si des accolades sont appariées incorrectement.

L’exemple suivant génère l’erreur C2935 :

```cpp
// C2935.cpp
// compile with: /c
template<class T>
struct TC {};
void TC<int>() {}   // C2935

// OK
struct TC2 {};
void TC2() {}
```

L’erreur C2935 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2935b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC { };
void GC<int>() {}   // C2935
void GC() {}   // OK
```
