---
title: Erreur du compilateur C3900 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3900
dev_langs:
- C++
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfbec5086cd034b56795f47504c029e975aa36b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039671"
---
# <a name="compiler-error-c3900"></a>Erreur du compilateur C3900

'membre' : non autorisé dans la portée actuelle

Blocs de propriété peuvent contenir des déclarations de fonction et les définitions de fonction inline. Aucuns autres fonctions membres ne sont autorisés dans les blocs de propriété. Aucune fonction typedefs, opérateurs ou friend n’est autorisées. Pour plus d'informations, consultez [property](../../windows/property-cpp-component-extensions.md).

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