---
description: 'En savoir plus sur : erreur du compilateur C2728'
title: Erreur du compilateur C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 7ef24dd037f8d765c072a61320da64411248dbc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245302"
---
# <a name="compiler-error-c2728"></a>Erreur du compilateur C2728

'type' : un tableau natif ne peut pas contenir ce type

La syntaxe de création de tableau a été utilisée pour créer un tableau d'objets managés ou WinRT. Vous ne pouvez pas créer un tableau d'objets managés ou WinRT à l'aide de la syntaxe du tableau natif.

Pour plus d'informations, consultez [tableau](../../extensions/arrays-cpp-component-extensions.md).

L'exemple suivant génère l'erreur C2728 et montre comment la corriger :

```cpp
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
