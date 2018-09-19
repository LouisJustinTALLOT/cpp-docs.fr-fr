---
title: Erreur du compilateur C3536 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7585a75ebe9733c228756e92d8e5ae57699aca27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088577"
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