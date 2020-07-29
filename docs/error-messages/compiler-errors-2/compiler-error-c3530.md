---
title: Erreur du compilateur C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 023d7f0a5d509c4b301a9985da8ea7feb1f3d203
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228828"
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

[Auto, mot clé](../../cpp/auto-keyword.md)
