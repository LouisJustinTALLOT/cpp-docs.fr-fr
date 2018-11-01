---
title: Erreur du compilateur C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 115e8cd63562964b19e4a67f7a649ecfab2596c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465258"
---
# <a name="compiler-error-c3156"></a>Erreur du compilateur C3156

'classe' : vous ne pouvez pas avoir de définition locale d'un type managé ou WinRT

Une fonction ne peut pas contenir la définition, ou la déclaration, d'une classe, d'un struct ou d'une interface managé(e) ou WinRT.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3156.

```
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
