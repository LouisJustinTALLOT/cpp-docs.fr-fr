---
title: Erreur du compilateur C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a16c5bd46d806d09861d5734b637c2c9d9b2f9d0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031894"
---
# <a name="compiler-error-c3536"></a>Erreur du compilateur C3536

'symbol' : ne peut pas être utilisé avant d’être initialisée

Le symbole indiqué ne peut pas être utilisé avant d’être initialisée. Dans la pratique, cela signifie qu'une variable ne peut pas être utilisée pour s'initialiser.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. N’initialisez pas une variable avec lui-même.

## <a name="example"></a>Exemple

L’exemple suivant donne C3536 parce que chaque variable est initialisée avec lui-même.

```
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