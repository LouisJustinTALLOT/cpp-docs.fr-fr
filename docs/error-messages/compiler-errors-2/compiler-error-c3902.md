---
description: 'En savoir plus sur : erreur du compilateur C3902'
title: Erreur du compilateur C3902
ms.date: 11/04/2016
f1_keywords:
- C3902
helpviewer_keywords:
- C3902
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
ms.openlocfilehash: 8d72b5e8f1e1494f18bda61c67ae2f5e38453f01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144272"
---
# <a name="compiler-error-c3902"></a>Erreur du compilateur C3902

'accessor' : le type du dernier paramètre doit être’type'

Le type du dernier paramètre d’au moins une méthode Set doit correspondre au type de la propriété. Pour plus d'informations, consultez [property](../../extensions/property-cpp-component-extensions.md).

L’exemple suivant génère l’C3902 :

```cpp
// C3902.cpp
// compile with: /clr /c
using namespace System;
ref class X {
   property String ^Name {
      void set(int);   // C3902
      // try the following line instead
      // void set(String^){}
   }

   property double values[int,int] {
      void set(int, int, float);   // C3902
      // try the following line instead
      // void set(int, int, double){}
   }
};
```
