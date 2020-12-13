---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4400'
title: Avertissement du compilateur (niveau 4) C4400
ms.date: 11/04/2016
f1_keywords:
- C4400
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
ms.openlocfilehash: c91a77758127b5c5b5c5ab742c980f6367830812
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136238"
---
# <a name="compiler-warning-level-4-c4400"></a>Avertissement du compilateur (niveau 4) C4400

'type' : les qualificateurs const/volatile sur ce type ne sont pas pris en charge

Les qualificateurs [const](../../cpp/const-cpp.md)et [volatile](../../cpp/volatile-cpp.md)ne fonctionnent pas avec les variables de types Common Language Runtime.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4400.

```cpp
// C4400.cpp
// compile with: /clr /W4
// C4401 expected
using namespace System;
#pragma warning (disable : 4101)
int main() {
   const String^ str;   // C4400
   volatile String^ str2;   // C4400
}
```
