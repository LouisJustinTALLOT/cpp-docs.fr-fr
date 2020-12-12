---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4460'
title: Avertissement du compilateur (niveau 4) C4460
ms.date: 11/04/2016
f1_keywords:
- C4460
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
ms.openlocfilehash: 68f38ad1ad65b27f35b79495bb2edd930c25d732
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334837"
---
# <a name="compiler-warning-level-4-c4460"></a>Avertissement du compilateur (niveau 4) C4460

paramètre de l'opérateur WinRT ou CLR 'opérateur' passé par référence. L'opérateur WinRT ou CLR 'opérateur' a une sémantique différente de celle de l'opérateur C++ 'opérateur', voulez-vous effectuer un passage par valeur ?

Vous avez passé une valeur par référence à un opérateur CLR ou Windows Runtime défini par l'utilisateur. Si la valeur est modifiée dans la fonction, notez que la valeur de retour de la fonction sera attribuée à la valeur retournée après l'appel de fonction. En C++ standard, la valeur modifiée est reflétée après l'appel de fonction.

## <a name="example"></a>Exemple

L'exemple suivant génère l'avertissement C4460 et montre comment le corriger.

```cpp
// C4460.cpp
// compile with: /W4 /clr
#include <stdio.h>

public value struct V {
   static V operator ++(V& me) {   // C4460
   // try the following line instead
   // static V operator ++(V me) {

      printf_s(__FUNCSIG__ " called\n");
      V tmp = me;
      me.m_i++;
      return tmp;
   }
   int m_i;
};

int main() {
   V v;
   v.m_i = 0;

   printf_s("%d\n", v.m_i);   // Should print 0
   v++;   // Translates to "v = V::operator ++(v)"
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning
}
```
