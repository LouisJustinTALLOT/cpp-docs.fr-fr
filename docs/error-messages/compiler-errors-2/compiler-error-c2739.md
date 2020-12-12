---
description: 'En savoir plus sur : erreur du compilateur C2739'
title: Erreur du compilateur C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 2a65f552eeb8a0b475b5559aaa3f1ab6b0da0e25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123082"
---
# <a name="compiler-error-c2739"></a>Erreur du compilateur C2739

'nombre' : les dimensions de tableau managé ou WinRT explicites doivent être comprises entre 1 et 32

Une dimension de tableau n'était pas comprise entre 1 et 32.

L'exemple suivant génère l'erreur C2739 et montre comment la corriger :

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
