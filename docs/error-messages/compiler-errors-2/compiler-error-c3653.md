---
title: Erreur du compilateur C3653
ms.date: 11/04/2016
f1_keywords:
- C3653
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
ms.openlocfilehash: 75e2c061190b24019491db7a625ecafb5ac82b6b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776442"
---
# <a name="compiler-error-c3653"></a>Erreur du compilateur C3653

'fonction' : ne peut pas être utilisé comme substitution nommée : fonction substituée introuvable ; n’auriez-vous pas oublié de nommer la fonction explicitement, à l’aide un :: opérateur ?

Une substitution explicite spécifié à une fonction qui est introuvable dans n’importe quelle interface. Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

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