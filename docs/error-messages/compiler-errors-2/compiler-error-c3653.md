---
title: Erreur du compilateur C3653
ms.date: 11/04/2016
f1_keywords:
- C3653
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
ms.openlocfilehash: d7936303dab4fbb273a01f98def5b9af99f89dac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477621"
---
# <a name="compiler-error-c3653"></a>Erreur du compilateur C3653

'fonction' : ne peut pas être utilisé comme substitution nommée : fonction substituée introuvable ; n’auriez-vous pas oublié de nommer la fonction explicitement, à l’aide un :: opérateur ?

Une substitution explicite spécifié à une fonction qui est introuvable dans n’importe quelle interface. Pour plus d’informations, consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3653 :

```
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