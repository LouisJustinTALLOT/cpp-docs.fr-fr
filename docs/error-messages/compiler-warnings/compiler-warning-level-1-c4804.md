---
title: Avertissement du compilateur (niveau 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 28b3e49717993a3bf20c8cfec5938d698266c0f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476074"
---
# <a name="compiler-warning-level-1-c4804"></a>Avertissement du compilateur (niveau 1) C4804

'opération' : utilisation risquée du type 'bool' dans l’opération

Cet avertissement se produit lorsque vous avez utilisé un `bool` variable ou une valeur de manière inattendue. Par exemple, C4804 est généré si vous utilisez des opérateurs tels que l’opérateur unaire négatif (**-**) ou l’opérateur de complément (`~`). Le compilateur évalue l’expression.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4804 :

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```