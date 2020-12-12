---
description: 'En savoir plus sur : erreur du compilateur C3653'
title: Erreur du compilateur C3653
ms.date: 11/04/2016
f1_keywords:
- C3653
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
ms.openlocfilehash: 6f41d52416d2fee05873197efa60e4b888cf29f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320103"
---
# <a name="compiler-error-c3653"></a>Erreur du compilateur C3653

'fonction' : ne peut pas être utilisé en tant que substitution nommée : fonction substituée introuvable ; avez-vous oublié de nommer la fonction explicitement, à l’aide d’un opérateur ::?

Une substitution explicite a spécifié une fonction qui n’a été trouvée dans aucune interface. Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’C3653 :

```cpp
// C3653.cpp
// compile with: /clr
public interface struct I {
   void h();
};

public ref struct X : public I {
   virtual void f() new sealed = J {};   // C3653 no J in scope
   virtual void g() {}   // OK
   virtual void h() new sealed = I::h {};   // OK
};
```
