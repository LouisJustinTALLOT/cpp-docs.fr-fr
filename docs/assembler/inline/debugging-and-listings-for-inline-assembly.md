---
title: Débogage et listes pour l’Assembly Inline | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6cca954ae15252b97d883ba8491fdb98e506f68
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689287"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Débogage et listes pour l'assembly inline

**Section spécifique à Microsoft**

Programmes contenant le code assembleur inline peuvent être débogués avec un débogueur au niveau de la source si vous compilez avec le [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) option.

Dans le débogueur, vous pouvez définir des points d'arrêt sur C ou C++ et des lignes en langage assembleur. Si vous activez le mode mixte assembly et source, vous pouvez consulter la source et le formulaire désassemblé du code assembleur.

Notez que mettre plusieurs instructions assembleur ou plusieurs instructions de langage source sur une ligne peut entraver le débogage. En mode source, vous pouvez utiliser le débogueur pour définir des points d'arrêt sur une ligne unique, mais pas sur des instructions individuelles sur la même ligne. Le même principe s'applique à un bloc `__asm` défini comme macro C, qui se développe en une seule ligne logique.

Si vous créez une source mixte et l’assembly annonce avec la [/FA](../../build/reference/fa-fa-listing-file.md) option du compilateur, la liste contient des formes de la source et l’assembly de chaque ligne en langage assembleur. Les macros ne sont pas développées dans les listes, mais elles sont développées pendant la compilation.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>