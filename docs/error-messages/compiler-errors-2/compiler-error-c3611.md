---
description: 'En savoir plus sur : erreur du compilateur C3611'
title: Erreur du compilateur C3611
ms.date: 11/04/2016
f1_keywords:
- C3611
helpviewer_keywords:
- C3611
ms.assetid: 42f3e320-41de-420a-bd05-8924cab765aa
ms.openlocfilehash: 9c18e8e757e3962af1f2e0fbcc0d33384f3b6329
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262293"
---
# <a name="compiler-error-c3611"></a>Erreur du compilateur C3611

'fonction' : une fonction sealed ne peut pas avoir de spécificateur pure

Une fonction sealed a été déclarée de manière incorrecte.  Pour plus d’informations, consultez [sealed](../../extensions/sealed-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3611.

```cpp
// C3611.cpp
// compile with: /clr /c

ref struct V {
   virtual void Test() sealed = 0;   // C3611
   virtual void Test2() sealed;   // OK
   virtual void Test3() = 0;   // OK
};
```
