---
title: Compilateur avertissement (niveau 4) C4210 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4210
dev_langs:
- C++
helpviewer_keywords:
- C4210
ms.assetid: f8600adf-dfe2-4022-a37a-3d4997641dfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2cd9bf209d7d9f48ac2ff0aae4663dc9088199df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017714"
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