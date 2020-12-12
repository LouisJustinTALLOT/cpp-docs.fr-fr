---
description: 'En savoir plus sur les éléments suivants : débogage et listes pour l’assembly inline'
title: Débogage et listes pour l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: b4608a0176de5e061d7dc7f15b8758d9bd3a94b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117868"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Débogage et listes pour l'assembly inline

**Spécifique à Microsoft**

Les programmes contenant du code assembleur inline peuvent être débogués à l’aide d’un débogueur de niveau source si vous compilez avec l’option [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .

Dans le débogueur, vous pouvez définir des points d'arrêt sur C ou C++ et des lignes en langage assembleur. Si vous activez le mode mixte assembly et source, vous pouvez consulter la source et le formulaire désassemblé du code assembleur.

Notez que mettre plusieurs instructions assembleur ou plusieurs instructions de langage source sur une ligne peut entraver le débogage. En mode source, vous pouvez utiliser le débogueur pour définir des points d'arrêt sur une ligne unique, mais pas sur des instructions individuelles sur la même ligne. Le même principe s’applique à un **`__asm`** bloc défini comme macro C, qui se développe en une seule ligne logique.

Si vous créez une liste mixte de sources et d’assemblys avec l’option de compilateur [/FAS](../../build/reference/fa-fa-listing-file.md) , la liste contient à la fois les formulaires source et d’assembly de chaque ligne en langage assembleur. Les macros ne sont pas développées dans les listes, mais elles sont développées pendant la compilation.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
