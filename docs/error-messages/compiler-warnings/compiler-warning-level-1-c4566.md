---
title: Avertissement du compilateur (niveau 1) C4566
ms.date: 11/04/2016
f1_keywords:
- C4566
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
ms.openlocfilehash: 87d610980ffe9d9e5087ddaec0ecb91d813a4d60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162256"
---
# <a name="compiler-warning-level-1-c4566"></a>Avertissement du compilateur (niveau 1) C4566

le caractère représenté par le nom de caractère universel’Char’ne peut pas être représenté dans la page de codes actuelle (page)

Tous les caractères Unicode ne peuvent pas être représentés dans votre page de codes ANSI actuelle.

Les chaînes étroites (caractères d’un octet) sont converties en caractères multioctets, contrairement aux chaînes larges (caractères de deux octets).

L’exemple suivant génère l’C4566 :

```cpp
// C4566.cpp
// compile with: /W1
int main() {
   char c1 = '\u03a0';   // C4566
   char c2 = '\u0642';   // C4566

   wchar_t c3 = L'\u03a0';   // OK
   wchar_t c4 = L'\u0642';   // OK
}
```
