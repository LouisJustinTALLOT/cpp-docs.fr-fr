---
description: 'En savoir plus sur : erreur du compilateur C2695'
title: Erreur du compilateur C2695
ms.date: 11/04/2016
f1_keywords:
- C2695
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
ms.openlocfilehash: 6137749725de5c2285cb5defd84fd7c8c0f2e237
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326641"
---
# <a name="compiler-error-c2695"></a>Erreur du compilateur C2695

'fonction1 ' : la fonction virtuelle de substitution diffère de’fonction2 'uniquement par la Convention d’appel

La signature d’une fonction dans une classe dérivée ne peut pas substituer une fonction dans une classe de base et modifier la Convention d’appel.

L’exemple suivant génère l’C2695 :

```cpp
// C2695.cpp
class C {
   virtual void __fastcall func();
};

class D : public C {
   virtual void __clrcall func();   // C2695
};
```
