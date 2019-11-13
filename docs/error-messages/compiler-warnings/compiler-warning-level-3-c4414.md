---
title: Avertissement du compilateur (niveau 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 43570cd43ca6e9d4f892dc577f615e9fa980e561
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051581"
---
# <a name="compiler-warning-level-3-c4414"></a>Avertissement du compilateur (niveau 3) C4414

'fonction' : saut court à la fonction converti en Near

Les sauts courts génèrent une instruction compact qui crée une branche vers une adresse dans une plage limitée de l’instruction. L’instruction comprend un décalage bref qui représente la distance entre le saut et l’adresse cible, la définition de fonction. Lors de la liaison, une fonction peut être déplacée ou soumise à des optimisations au moment de l’édition de liens qui entraînent le déplacement de la fonction hors de la plage accessible à partir d’un décalage court. Le compilateur doit générer un enregistrement spécial pour le saut, ce qui nécessite que l’instruction jmp soit proche ou loin. Le compilateur a effectué la conversion.

Par exemple, le code suivant génère C4414 :

```cpp
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```