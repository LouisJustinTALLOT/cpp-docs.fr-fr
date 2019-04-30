---
title: Erreur du compilateur C3901
ms.date: 11/04/2016
f1_keywords:
- C3901
helpviewer_keywords:
- C3901
ms.assetid: 19af4141-39ad-4c16-a68f-3ae76f648186
ms.openlocfilehash: 31fbb1e89a0619b4dc8b3f6c86f7f6bc748b80d6
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344582"
---
# <a name="compiler-error-c3901"></a>Erreur du compilateur C3901

'fonction_accès' : doit avoir le type de retour 'type'

Type de retour de la méthode get au moins un doit correspondre au type de propriété. Pour plus d'informations, consultez [property](../../extensions/property-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3901 :

```
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