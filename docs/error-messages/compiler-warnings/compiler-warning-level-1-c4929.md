---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4929'
title: Avertissement du compilateur (niveau 1) C4929
ms.date: 11/04/2016
f1_keywords:
- C4929
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
ms.openlocfilehash: 73331759ebdf43694618140985161400ecdafb1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203547"
---
# <a name="compiler-warning-level-1-c4929"></a>Avertissement du compilateur (niveau 1) C4929

'file' : TypeLibrary contient une Union ; qualificateur’embedded_idl’ignoré

L’attribut embedded_idl de [#import](../../preprocessor/hash-import-directive-cpp.md) n’a pas pu être appliqué à la bibliothèque de types, car une Union est présente dans la bibliothèque de types. Pour résoudre cet avertissement, n’utilisez pas embedded_idl.

## <a name="examples"></a>Exemples

L’exemple suivant définit un composant.

```cpp
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

L’exemple suivant génère l’C4929.

```cpp
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```
