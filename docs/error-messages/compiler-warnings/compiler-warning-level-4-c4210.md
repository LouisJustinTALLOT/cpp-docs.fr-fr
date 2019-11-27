---
title: Avertissement du compilateur (niveau 4) C4210
ms.date: 11/04/2016
f1_keywords:
- C4210
helpviewer_keywords:
- C4210
ms.assetid: f8600adf-dfe2-4022-a37a-3d4997641dfd
ms.openlocfilehash: 5b27a711187af21dac093bdcc3e3af84502fe153
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541852"
---
# <a name="compiler-warning-level-4-c4210"></a>Avertissement du compilateur (niveau 4) C4210

extension non standard utilisée : portée de fichier donnée à la fonction

Avec les extensions Microsoft par défaut ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)), les déclarations de fonction ont une portée de fichier.

```c
// C4210.c
// compile with: /W4 /c
void func1()
{
   extern int func2( double );   // C4210 expected
}

int main()
{
   func2( 4 );   //  /Ze passes 4 as type double
}                //  /Za passes 4 as type int
```

Cette extension peut empêcher votre code d’être portable vers d’autres compilateurs.