---
title: Erreur du compilateur C3903
ms.date: 11/04/2016
f1_keywords:
- C3903
helpviewer_keywords:
- C3903
ms.assetid: cf47d7ad-a3bd-4f75-a253-71586e7a3be6
ms.openlocfilehash: bed6561d1e8d4281cd57e78808744d018c3cc9b3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778889"
---
# <a name="compiler-error-c3903"></a>Erreur du compilateur C3903

'property' : est a pas set ou get, méthode

Une propriété doit avoir au moins un `get` ou un `set` (méthode). Pour plus d'informations, consultez [property](../../extensions/property-cpp-component-extensions.md).

L’exemple suivant génère C3903 :

```
// C3903.cpp
// compile with: /clr
ref class X {
   property int P {
      void f(int){}
      // Add one or both of the following lines.
      // void set(int){}
      // int get(){return 0;}
   };   // C3903

   property double Q[,,,,] {
      void f(){}
      // Add one or both of the following lines.
      // void set(int, char, int, char, double, double){}
      // double get(int, char, int, char, double){return 1.1;}
   }   // C3903
};
```