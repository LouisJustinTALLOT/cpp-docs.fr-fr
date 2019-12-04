---
title: Erreur du compilateur C2776
ms.date: 11/04/2016
f1_keywords:
- C2776
helpviewer_keywords:
- C2776
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
ms.openlocfilehash: 79758c88e595e6d5ebb5cd4b39a8df8fc1339752
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740063"
---
# <a name="compiler-error-c2776"></a>Erreur du compilateur C2776

une seule méthode' « obtient » peut être spécifiée par propriété

Vous ne pouvez spécifier qu’une seule fonction de `get` dans l’attribut étendu de [propriété](../../cpp/property-cpp.md) . Cette erreur se produit lorsque plusieurs fonctions de `get` sont spécifiées.

L’exemple suivant génère l’C2776 :

```cpp
// C2776.cpp
struct A {
   __declspec(property(get=GetProp,get=GetPropToo))
   // try the following line instead
   // __declspec(property(get=GetProp))
      int prop;   // C2776
   int GetProp(void);
   int GetPropToo(void);
};
```
