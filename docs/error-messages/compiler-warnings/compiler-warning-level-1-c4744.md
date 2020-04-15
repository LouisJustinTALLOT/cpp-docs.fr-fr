---
title: Avertissement du compilateur (niveau 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f932b1bcdf011678d4f85e0edf1e116a954b59fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367376"
---
# <a name="compiler-warning-level-1-c4744"></a>Avertissement du compilateur (niveau 1) C4744

'var' a un type différent dans 'fichier1' et 'file2': 'type1' et 'type2'

Une variable externe référencée ou définie dans deux fichiers a différents types dans ces fichiers.  Pour résoudre, soit faire les définitions de type les mêmes, ou changer le nom variable dans l’un des fichiers.

C4744 n’est émis que lorsque les fichiers sont compilés avec /GL.  Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
> C4744 se produit habituellement dans les fichiers C (et non C), car dans le C, un nom variable est décoré d’informations de type.  Lorsque l’échantillon (ci-dessous) est compile sous le forme de C, vous obtiendrez l’erreur de liaison LNK2019.

## <a name="example"></a>Exemple

Cet échantillon contient la première définition.

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Exemple

L’échantillon suivant génère du C4744.

```c
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```
