---
title: Erreur du compilateur C3532 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3532
dev_langs:
- C++
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25562a83845690cf923784ee27e20fd109c1c832
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109637"
---
# <a name="compiler-error-c3532"></a>Erreur du compilateur C3532

'type' : utilisation incorrecte de 'auto'

Le type indiqué ne peut pas être déclaré avec le `auto` mot clé. Par exemple, vous ne pouvez pas utiliser le `auto` mot clé pour déclarer un tableau ou une méthode de type de retour.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Assurez-vous que l’expression d’initialisation génère un type valid.

1. Assurez-vous que vous ne déclarez pas un tableau ou un type de retour de méthode.

## <a name="example"></a>Exemple

L’exemple suivant donne C3532 parce que le `auto` mot clé ne peut pas déclarer un type de retour de méthode.

```
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Exemple

L’exemple suivant donne C3532 parce que le `auto` mot clé ne peut pas déclarer un tableau.

```
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>Voir aussi

[auto, mot clé](../../cpp/auto-keyword.md)