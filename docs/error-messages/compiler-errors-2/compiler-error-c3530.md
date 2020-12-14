---
description: 'En savoir plus sur : erreur du compilateur C3530'
title: Erreur du compilateur C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 74cd9ade2805ba26c700d476c53f87ea86a3baba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315372"
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
