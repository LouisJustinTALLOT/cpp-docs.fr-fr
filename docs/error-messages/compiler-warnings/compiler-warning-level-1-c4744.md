---
title: Avertissement du compilateur (niveau 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f6954ae7966edf200249bb5d10f0dfb011bcef22
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051560"
---
# <a name="compiler-warning-level-1-c4744"></a>Avertissement du compilateur (niveau 1) C4744

'var’a un type différent dans’fichier1 'et’fichier2 ' : 'type1 'et’type2 '

Une variable externe référencée ou définie dans deux fichiers a des types différents dans ces fichiers.  Pour résoudre ce type de fichier, faites en sorte que les définitions de type soient identiques ou modifiez le nom de la variable dans l’un des fichiers.

C4744 est émis uniquement lorsque des fichiers sont compilés avec/GL.  Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
>  C4744 se produit généralement dans les fichiers C++C (not), C++ car dans un nom de variable est décoré avec les informations de type.  Lorsque l’exemple (ci-dessous) est compilé en C++tant que, vous obtenez l’erreur de l’éditeur de liens LNK2019.

## <a name="example"></a>Exemple

Cet exemple contient la première définition.

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4744.

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