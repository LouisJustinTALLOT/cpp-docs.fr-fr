---
title: Erreur du compilateur C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: 35df94ccfcd7942f9057cb37ceee349c09b80607
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777413"
---
# <a name="compiler-error-c3900"></a>Erreur du compilateur C3900

'membre' : non autorisé dans la portée actuelle

Blocs de propriété peuvent contenir des déclarations de fonction et les définitions de fonction inline. Aucuns autres fonctions membres ne sont autorisés dans les blocs de propriété. Aucune fonction typedefs, opérateurs ou friend n’est autorisées. Pour plus d'informations, consultez [property](../../extensions/property-cpp-component-extensions.md).

Définitions d’événement ne peuvent contenir que des méthodes d’accès et des fonctions.

L’exemple suivant génère C3900 :

```
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

L’exemple suivant génère C3900 :

```
// C3900b.cpp
// compile with: /clr
using namespace System;
delegate void H();
ref class X {
   event H^ E {
      int m;   // C3900

      // OK
      void Test() {}

      void add( H^ h ) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```