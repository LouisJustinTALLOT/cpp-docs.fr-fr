---
title: Erreur du compilateur C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 4b0c019b2425b314f5b3503db41042d917283aa8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758175"
---
# <a name="compiler-error-c3665"></a>Erreur du compilateur C3665

'destructeur' : spécificateur de substitution’MotClé’non autorisé sur un destructeur/finaliseur

Un mot clé qui n’est pas autorisé sur un destructeur ou un finaliseur a été utilisé.

Par exemple, un nouvel emplacement ne peut pas être demandé sur un destructeur ou un finaliseur.  Pour plus d’informations, consultez substitutions et destructeurs [explicites](../../extensions/explicit-overrides-cpp-component-extensions.md) [et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

L’exemple suivant génère l’C3665 :

```cpp
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
