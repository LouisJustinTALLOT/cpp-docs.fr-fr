---
title: Erreur du compilateur C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a140847b642ac2437b67aa957328c3b8fbfc592d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761567"
---
# <a name="compiler-error-c3536"></a>Erreur du compilateur C3536

'Symbol' : ne peut pas être utilisé avant d’être initialisé

Le symbole indiqué ne peut pas être utilisé avant d’être initialisé. Dans la pratique, cela signifie qu'une variable ne peut pas être utilisée pour s'initialiser.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. N’initialisez pas une variable avec elle-même.

## <a name="example"></a>Exemple

L’exemple suivant génère C3536, car chaque variable est initialisée avec elle-même.

```cpp
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>Voir aussi

[auto, mot clé](../../cpp/auto-keyword.md)
