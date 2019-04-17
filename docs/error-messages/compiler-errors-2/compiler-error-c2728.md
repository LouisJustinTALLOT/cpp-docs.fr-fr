---
title: Erreur du compilateur C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 1fbbc3d63386ebe98a447de8b7166a5263d2168f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767416"
---
# <a name="compiler-error-c2728"></a>Erreur du compilateur C2728

'type' : un tableau natif ne peut pas contenir ce type

La syntaxe de création de tableau a été utilisée pour créer un tableau d'objets managés ou WinRT. Vous ne pouvez pas créer un tableau d'objets managés ou WinRT à l'aide de la syntaxe du tableau natif.

Pour plus d'informations, consultez [tableau](../../extensions/arrays-cpp-component-extensions.md).

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
