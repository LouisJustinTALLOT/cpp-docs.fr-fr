---
description: 'En savoir plus sur : erreur du compilateur C3536'
title: Erreur du compilateur C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: 62bd8bb75adfbf0e21f150f4240bb5f4011f6382
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112503"
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

[Auto, mot clé](../../cpp/auto-cpp.md)
