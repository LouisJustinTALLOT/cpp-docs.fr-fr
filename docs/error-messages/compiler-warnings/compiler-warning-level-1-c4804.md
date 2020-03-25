---
title: Avertissement du compilateur (niveau 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 3f1b349599c77bc001911431fe0d83496ca3dfce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199405"
---
# <a name="compiler-warning-level-1-c4804"></a>Avertissement du compilateur (niveau 1) C4804

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
