---
description: 'En savoir plus sur : erreur du compilateur C3901'
title: Erreur du compilateur C3901
ms.date: 11/04/2016
f1_keywords:
- C3901
helpviewer_keywords:
- C3901
ms.assetid: 19af4141-39ad-4c16-a68f-3ae76f648186
ms.openlocfilehash: b69897133dc787986dc8e1b750b64fdca35ad85f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222643"
---
# <a name="compiler-error-c3901"></a>Erreur du compilateur C3901

'accessor_function' : doit avoir le type de retour’type'

Au moins un type de retour de la méthode d’extraction doit correspondre au type de propriété. Pour plus d'informations, consultez [property](../../extensions/property-cpp-component-extensions.md).

L’exemple suivant génère l’C3901 :

```cpp
// C3901.cpp
// compile with: /clr /c
using namespace System;
ref class X {
   property String^ Name {
      void get();   // C3901
      // try the following line instead
      // String^ get();
   };
};

ref class Y {
   property double values[int, int] {
      int get(int, int);   // C3901
      // try the following line instead
      // double get(int, int);
   };
};
```
