---
title: Erreur du compilateur C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 3e3584d5e9166bb57e3be56e33f0198cacace7c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615174"
---
# <a name="compiler-error-c2728"></a>Erreur du compilateur C2728

'type' : un tableau natif ne peut pas contenir ce type

La syntaxe de création de tableau a été utilisée pour créer un tableau d'objets managés ou WinRT. Vous ne pouvez pas créer un tableau d'objets managés ou WinRT à l'aide de la syntaxe du tableau natif.

Pour plus d'informations, consultez [tableau](../../windows/arrays-cpp-component-extensions.md).

L'exemple suivant génère l'erreur C2728 et montre comment la corriger :

```
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
