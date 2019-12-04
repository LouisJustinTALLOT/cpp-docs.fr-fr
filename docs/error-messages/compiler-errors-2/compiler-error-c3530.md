---
title: Erreur du compilateur C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 3766eaa83457ba6cffaf8b1599983a065772911c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750141"
---
# <a name="compiler-error-c3530"></a>Erreur du compilateur C3530

'auto’ne peut pas être combiné avec un autre spécificateur de type

Un spécificateur de type est utilisé avec le mot clé `auto`.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. N’utilisez pas de spécificateur de type dans une déclaration de variable qui utilise le mot clé `auto`.

## <a name="example"></a>Exemple

L’exemple suivant génère C3530, car la variable `x` est déclarée avec le mot clé `auto` et le type `int`, et parce que l’exemple est compilé avec **/Zc : auto**.

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

[auto, mot clé](../../cpp/auto-keyword.md)
