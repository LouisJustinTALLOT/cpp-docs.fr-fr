---
title: Erreur du compilateur C2857 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49e94e12b4cdf07d9f7fe74dd481bbc032a937eb
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601377"
---
# <a name="compiler-error-c2857"></a>Erreur du compilateur C2857

> ' #include ' instruction spécifiée avec le/Yc*filename* option de ligne de commande est introuvable dans le fichier source

Le [/Yc](../../build/reference/yc-create-precompiled-header-file.md) option spécifie le nom d’un fichier include qui n’est pas inclus dans le fichier source en cours de compilation.

## <a name="remarks"></a>Notes

Lorsque vous utilisez le **/Yc**<em>filename</em> option sur un fichier source pour créer un fichier d’en-tête précompilé (PCH), que le fichier source doit inclure le *nom de fichier* fichier d’en-tête. Chaque fichier inclus dans le fichier source, y compris le texte spécifié *filename*, est inclus dans le fichier d’en-tête Précompilé. Dans d’autres fichiers de code source compilés à l’aide de la **/Yu**<em>filename</em> permet d’utiliser l’en-tête Précompilé du fichier, un include de *filename* doit être la première ligne sans commentaire dans le fichier. Le compilateur ignore quoi que ce soit dans le fichier source avant cette include.

Cette erreur peut être provoquée par un `#include "filename"` instruction dans un bloc de compilation conditionnelle n’est pas compilé dans votre fichier de source de fichier PCH.

## <a name="example"></a>Exemple

En règle générale, un fichier source dans votre projet est désigné en tant que fichier PCH source et un fichier d’en-tête est utilisé en tant que le fichier d’en-tête PCH. Un fichier d’en-tête PCH classique comprend tous les en-têtes de bibliothèque utilisés dans votre projet, mais les en-têtes non locales qui sont en cours de développement. Dans cet exemple, le fichier d’en-tête PCH nommé *my_pch.h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

Le fichier de source de fichier PCH est compilé à l’aide de la **/Yc**<em>my_pch.h</em> option. Si le compilateur ne trouve pas un include de ce fichier d’en-tête PCH, il génère C2857 :

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

Pour utiliser ce fichier PCH, les fichiers source doivent être compilés à l’aide de la **/Yu**<em>my_pch.h</em> option. Le fichier d’en-tête PCH doit être tout d’abord inclus dans les fichiers sources qui utilisent l’en-tête Précompilé :

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