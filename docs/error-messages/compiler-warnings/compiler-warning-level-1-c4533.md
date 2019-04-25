---
title: Avertissement du compilateur (niveau 1) C4533
ms.date: 11/04/2016
f1_keywords:
- C4533
helpviewer_keywords:
- C4533
ms.assetid: 359fecda-d540-46e5-b214-dbabe9ef50d2
ms.openlocfilehash: 8ac7f00ad3401e88224c0150324822ce71e95018
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160768"
---
# <a name="compiler-warning-level-1-c4533"></a>Avertissement du compilateur (niveau 1) C4533

l’initialisation de 'variable' est ignorée par 'instruction'

Une instruction dans votre programme modifié le flux de contrôle, telles qu’une instruction qui a initialisé une variable n’a pas été exécutée. L’exemple suivant génère l’erreur C4533 :

```
// C4533.cpp
// compile with: /W1
#include <stdio.h>

struct A
{
   int m_data;
};

int main()
{
   if (1)
   {
      goto Label;
   }

   A a = { 100 };

   Label:   // C4533
      printf("\n%d", a.m_data);   // prints an uninitialized value
}
```