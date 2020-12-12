---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4556'
title: Avertissement du compilateur (niveau 1) C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: a0e0780b541b74125135ab84daa6ecab80b57e83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265855"
---
# <a name="compiler-warning-level-1-c4556"></a>Avertissement du compilateur (niveau 1) C4556

> la valeur de l’argument immédiat *intrinsèque'**value*'est en dehors de la limite  -  

## <a name="remarks"></a>Notes

Un intrinsèque correspond à une instruction matérielle. L’instruction matérielle a un nombre fixe de bits pour encoder la constante. Si la *valeur* est hors limites, elle n’est pas encodée correctement. Le compilateur tronque les bits supplémentaires.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4556 :

```cpp
// C4556.cpp
// compile with: /W1
// processor: x86 IPF
#include <xmmintrin.h>

void test()
{
   __m64 m;
   _m_pextrw(m, 5);   // C4556
}

int main()
{
}
```
