---
title: Avertissement du compilateur (niveau 1) C4550
ms.date: 11/04/2016
f1_keywords:
- C4550
helpviewer_keywords:
- C4550
ms.assetid: f902b4ed-5f17-48ea-b693-92f4fb8c8054
ms.openlocfilehash: 454b0154f555ef1ba1ac13ea7a87d454d59c6f05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186164"
---
# <a name="compiler-warning-level-1-c4550"></a>Avertissement du compilateur (niveau 1) C4550

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
