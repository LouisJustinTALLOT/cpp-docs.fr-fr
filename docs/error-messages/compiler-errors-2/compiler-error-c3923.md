---
description: 'En savoir plus sur : erreur du compilateur C3923'
title: Erreur du compilateur C3923
ms.date: 11/04/2016
f1_keywords:
- C3923
helpviewer_keywords:
- C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
ms.openlocfilehash: 261ff6d5a3d7f6a246d906b1d91809d8764ca2bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220693"
---
# <a name="compiler-error-c3923"></a>Erreur du compilateur C3923

'membre' : les définitions de classes, de structures ou d'unions locales ne sont pas autorisées dans une fonction membre d'une classe managée ou WinRT

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3923.

```cpp
// C3923.cpp
// compile with: /clr /c
ref struct x {
   void Test() {
      struct a {};   // C3923
      class b {};   // C3923
      union c {};   // C3923
   }
};
```
