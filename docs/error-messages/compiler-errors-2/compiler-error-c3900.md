---
description: 'En savoir plus sur : erreur du compilateur C3900'
title: Erreur du compilateur C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: 7b210eb6369b8953f36821d45690de8656113af2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238931"
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
