---
title: Avertissement du compilateur (niveau 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 97ad076325b11329896d98367fb3ac311ec5ded9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051571"
---
# <a name="compiler-warning-level-1-c4804"></a>Avertissement du compilateur (niveau 1) C4804

'Operation' : utilisation risquée du type’bool’dans l’opération

Cet avertissement s’utilise quand vous avez utilisé une variable ou une valeur `bool` de façon inattendue. Par exemple, C4804 est généré si vous utilisez des opérateurs tels que l’opérateur unaire négatif ( **-** ) ou l’opérateur de complément (`~`). Le compilateur évalue l’expression.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4804 :

```cpp
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