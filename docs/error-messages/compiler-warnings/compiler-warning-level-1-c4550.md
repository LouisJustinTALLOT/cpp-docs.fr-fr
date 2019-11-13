---
title: Avertissement du compilateur (niveau 1) C4550
ms.date: 11/04/2016
f1_keywords:
- C4550
helpviewer_keywords:
- C4550
ms.assetid: f902b4ed-5f17-48ea-b693-92f4fb8c8054
ms.openlocfilehash: 1c310855ee3925374de8b736cde9013d48df6482
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966377"
---
# <a name="compiler-warning-level-1-c4550"></a>Avertissement du compilateur (niveau 1) C4550

l’expression prend la valeur d’une fonction qui n’a pas de liste d’arguments

Il manque une liste d’arguments dans un pointeur déréférencé vers une fonction.

## <a name="example"></a>Exemple

```cpp
// C4550.cpp
// compile with: /W1
bool f()
{
   return true;
}

typedef bool (*pf_t)();

int main()
{
   pf_t pf = f;
   if (*pf) {}  // C4550
   return 0;
}
```