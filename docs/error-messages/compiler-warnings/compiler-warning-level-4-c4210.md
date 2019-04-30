---
title: Avertissement du compilateur (niveau 4) C4210
ms.date: 11/04/2016
f1_keywords:
- C4210
helpviewer_keywords:
- C4210
ms.assetid: f8600adf-dfe2-4022-a37a-3d4997641dfd
ms.openlocfilehash: 3435e18f60568cad390dcb0ef7900658a21ea959
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401187"
---
# <a name="compiler-warning-level-4-c4210"></a>Avertissement du compilateur (niveau 4) C4210

extension non standard utilisée : portée du fichier accordée (fonction)

Avec les extensions Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)), les déclarations de fonction ont une portée de fichier.

```
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

Cette extension peut empêcher votre code d’autres compilateurs.