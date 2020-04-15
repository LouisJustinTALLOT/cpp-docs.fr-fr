---
title: Assembleur inline
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++]
- assembler [C++], inline
- assembly language [C++], inline
- inline assembler [C++]
- inline assembly [C++]
ms.assetid: 7e13f18f-3628-4306-8b81-4a6d09c043fe
ms.openlocfilehash: 2050f59601755a93c73b743debacbf52ba9cec05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318073"
---
# <a name="inline-assembler"></a>Assembleur inline

**Microsoft Spécifique**

Le langage assembleur atteint de nombreux objectifs, tels que l'amélioration de la vitesse du programme, la réduction des besoins en mémoire et le contrôle du matériel. Vous pouvez utiliser l'assembleur inline pour incorporer des instructions en langage assembleur directement dans vos programmes sources C et C++ sans code assembleur ni étapes de liaison supplémentaires. L'assembleur inline est intégré au compilateur. Par conséquent, vous n'avez pas besoin d'assembleur distinct tel que MASM (Microsoft Macro Assembler).

> [!NOTE]
> Les programmes avec du code assembleur inline ne sont pas entièrement portables sur d'autres plateformes matérielles. Si vous concevez pour la portabilité, évitez d'utiliser l'assembleur inline.

L’assemblage en ligne n’est pas pris en charge sur les processeurs ARM et x64.  Les rubriques suivantes expliquent comment utiliser l'assembleur inline de Visual C/C++ avec des processeurs x86 :

- [Vue d'ensemble de l'assembleur inline](../../assembler/inline/inline-assembler-overview.md)

- [Avantages de l'assembly inline](../../assembler/inline/advantages-of-inline-assembly.md)

- [__asm](../../assembler/inline/asm.md)

- [Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)

- [Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)

- [Utilisation et conservation des registres dans un assembly inline](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)

- [Accès aux étiquettes dans l'assembly inline](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)

- [Appel des fonctions C dans l'assembly inline](../../assembler/inline/calling-c-functions-in-inline-assembly.md)

- [Appel aux fonctions CMD dans l’Assemblée Inline](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)

- [Définition des blocs __asm sous forme de macros C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)

- [Optimisation de l'assembly inline](../../assembler/inline/optimizing-inline-assembly.md)

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[Compiler Intrinsèques et Langue d’assemblage](../../intrinsics/compiler-intrinsics-and-assembly-language.md)<br/>
[Référence linguistique de CMD](../../cpp/cpp-language-reference.md)<br/>
