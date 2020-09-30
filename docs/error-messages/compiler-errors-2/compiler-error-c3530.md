---
title: Erreur du compilateur C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 152157824cb270f32b1233f39225abab7741eda5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507053"
---
# <a name="compiler-error-c3530"></a>Erreur du compilateur C3530

'auto’ne peut pas être combiné avec un autre spécificateur de type

Un spécificateur de type est utilisé avec le **`auto`** mot clé.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. N’utilisez pas de spécificateur de type dans une déclaration de variable qui utilise le **`auto`** mot clé.

## <a name="example"></a>Exemple

L’exemple suivant génère C3530, car la variable `x` est déclarée avec le **`auto`** mot clé et le type **`int`** , et parce que l’exemple est compilé avec **/Zc : auto**.

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Auto, mot clé](../../cpp/auto-cpp.md)
