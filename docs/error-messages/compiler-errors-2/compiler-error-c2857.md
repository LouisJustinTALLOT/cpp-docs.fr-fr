---
title: Erreur du compilateur C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 11b620f9748ac85e731d79b0652c0392375b2ea4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201849"
---
# <a name="compiler-error-c2857"></a>Erreur du compilateur C2857

> l’instruction' #include’spécifiée avec l’option de ligne de commande/YC*filename* est introuvable dans le fichier source

L’option [/Yc](../../build/reference/yc-create-precompiled-header-file.md) spécifie le nom d’un fichier include qui n’est pas inclus dans le fichier source en cours de compilation.

## <a name="remarks"></a>Notes

Lorsque vous utilisez l’option **/Yc**<em>filename</em> sur un fichier source pour créer un fichier d’en-tête précompilé (PCH), ce fichier source doit inclure le fichier d’en-tête de *nom* de fichier. Chaque fichier inclus dans le fichier source, jusqu’à et y compris le *nom*de fichier spécifié, est inclus dans le fichier PCH. Dans les autres fichiers sources compilés à l’aide de l’option **/Yu**<em>filename</em> pour utiliser le fichier PCH, un include de *filename* doit être la première ligne sans commentaire dans le fichier. Le compilateur ignore tout ce qui se trouve dans le fichier source avant que celle-ci soit incluse.

Cette erreur peut être causée par une instruction `#include "filename"` dans un bloc de compilation conditionnelle qui n’est pas compilé dans votre fichier source PCH.

## <a name="example"></a>Exemple

Dans l’utilisation courante, un fichier source de votre projet est désigné comme fichier source PCH et un fichier d’en-tête est utilisé comme fichier d’en-tête PCH. Un fichier d’en-tête PCH type contient tous les en-têtes de bibliothèque utilisés dans votre projet, mais pas les en-têtes locaux qui sont toujours en cours de développement. Dans cet exemple, le fichier d’en-tête PCH est nommé *my_pch. h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

Le fichier source PCH est compilé à l’aide de l’option **/yc**<em>my_pch. h</em> . Si le compilateur ne trouve pas d’inclusion de ce fichier d’en-tête PCH, il génère C2857 :

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

Pour utiliser ce fichier PCH, les fichiers sources doivent être compilés à l’aide de l’option **/yu**<em>my_pch. h</em> . Le fichier d’en-tête PCH doit être inclus en premier dans les fichiers sources qui utilisent le fichier PCH :

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```
