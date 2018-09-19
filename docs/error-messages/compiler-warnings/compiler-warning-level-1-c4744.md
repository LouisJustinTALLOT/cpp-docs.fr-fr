---
title: Compilateur avertissement (niveau 1) C4744 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1754977486327e06fb56a786be523c1b2fb7b917
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068973"
---
# <a name="compiler-warning-level-1-c4744"></a>Avertissement du compilateur (niveau 1) C4744

'var' a un type différent dans 'fichier1' et 'fichier2' : 'type1' et 'type2'

Une variable externe référencée ou définie dans deux fichiers possède différents types dans ces fichiers.  Pour résoudre, soit vous les définitions de type, ou modifier le nom de variable dans un des fichiers.

C4744 est émis uniquement lorsque les fichiers sont compilés avec /GL.  Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
>  C4744 se produit généralement dans les fichiers C (pas C++), car en C++, un nom de variable est décoré avec les informations de type.  Une fois l’exemple (ci-dessous) compile en C++, vous obtiendrez l’erreur de l’éditeur de liens LNK2019.

## <a name="example"></a>Exemple

Cet exemple contient la première définition.

```
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4744.

```
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