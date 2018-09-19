---
title: Erreur du compilateur C3901 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3901
dev_langs:
- C++
helpviewer_keywords:
- C3901
ms.assetid: 19af4141-39ad-4c16-a68f-3ae76f648186
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7027b73c4d8899adb8b644fc52208780b996eab9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085574"
---
# <a name="compiler-error-c3901"></a>Erreur du compilateur C3901

'fonction_accès' : doit avoir le type de retour 'type'

Type de retour de la méthode get au moins un doit correspondre au type de propriété. Pour plus d'informations, consultez [property](../../windows/property-cpp-component-extensions.md).

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