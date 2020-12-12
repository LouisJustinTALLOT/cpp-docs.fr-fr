---
description: 'En savoir plus sur : erreur du compilateur C3804'
title: Erreur du compilateur C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: b033acefd9a583b1659755f63fdbd3781fc95ccd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291504"
---
# <a name="compiler-error-c3804"></a>Erreur du compilateur C3804

'property_accessor' : les méthodes d’accesseur pour une propriété doivent être toutes statiques ou non statiques

Lors de la définition d’une propriété non triviale, les fonctions d’accesseur peuvent être statiques ou d’instance, mais pas les deux.

Pour plus d’informations, consultez [property](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3804.

```cpp
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
