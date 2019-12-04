---
title: Erreur du compilateur C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: f1289fb9a4d60f2c75b54fd573c83064f1517282
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749098"
---
# <a name="compiler-error-c3900"></a>Erreur du compilateur C3900

'membre' : non autorisé dans la portée actuelle

Les blocs de propriété peuvent contenir uniquement des déclarations de fonction et des définitions de fonction Inline. Aucun membre autre que Functions n’est autorisé dans les blocs de propriété. Aucun typedefs, opérateur ou fonction friend n’est autorisé. Pour plus d'informations, consultez [property](../../extensions/property-cpp-component-extensions.md).

Les définitions d’événements peuvent contenir uniquement des méthodes d’accès et des fonctions.

L’exemple suivant génère l’C3900 :

```cpp
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

L’exemple suivant génère l’C3900 :

```cpp
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
