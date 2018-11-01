---
title: Erreur du compilateur C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 30aaf67ac9f912059bb5726681e61feabc1e557d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644117"
---
# <a name="compiler-error-c3665"></a>Erreur du compilateur C3665

'destructeur' : spécificateur 'mot_clé' non autorisé sur un destructeur/finaliseur de substitution

Un mot clé a été utilisé qui n’est pas autorisée sur un destructeur ou un finaliseur.

Par exemple, un nouvel emplacement ne peut pas être demandé sur un destructeur ou un finaliseur.  Pour plus d’informations, consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md) et [destructeurs et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

L’exemple suivant génère l’erreur C3665 :

```
// C3665.cpp
// compile with: /clr
public ref struct R {
   virtual ~R() { }
   virtual void a() { }
};

public ref struct S : R {
   virtual ~S() new {}   // C3665
   virtual void a() new {}   // OK
};
```