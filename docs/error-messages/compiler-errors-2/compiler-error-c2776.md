---
description: 'En savoir plus sur : erreur du compilateur C2776'
title: Erreur du compilateur C2776
ms.date: 11/04/2016
f1_keywords:
- C2776
helpviewer_keywords:
- C2776
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
ms.openlocfilehash: 75e0121c61fd55aa89e6ffcc6e1ed00137fcaaca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298134"
---
# <a name="compiler-error-c2776"></a>Erreur du compilateur C2776

une seule méthode' « obtient » peut être spécifiée par propriété

Vous ne pouvez spécifier qu’une seule `get` fonction dans l’attribut étendu de [propriété](../../cpp/property-cpp.md) . Cette erreur se produit lorsque plusieurs `get` fonctions sont spécifiées.

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
