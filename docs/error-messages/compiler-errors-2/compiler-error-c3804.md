---
title: Erreur du compilateur C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: c3c00d1d07306a9e8dc67d3f75a5cb25d8f03aee
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770290"
---
# <a name="compiler-error-c3804"></a>Erreur du compilateur C3804

'accesseur_propriété' : les méthodes d’accesseur pour une propriété doit être toutes statiques ou non statiques

Lorsque vous définissez une propriété non triviale, les fonctions d’accesseur peuvent être statiques ou instance, mais pas les deux.

Pour plus d'informations, voir [property](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère C3804.

```
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```