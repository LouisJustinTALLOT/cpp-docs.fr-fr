---
description: 'En savoir plus sur : erreur du compilateur C3156'
title: Erreur du compilateur C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 265e887a7d075267e7a46d47d6bae9621bd83656
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174141"
---
# <a name="compiler-error-c3156"></a>Erreur du compilateur C3156

'classe' : vous ne pouvez pas avoir de définition locale d'un type managé ou WinRT

Une fonction ne peut pas contenir la définition, ou la déclaration, d'une classe, d'un struct ou d'une interface managé(e) ou WinRT.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3156.

```cpp
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
