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
ms.openlocfilehash: f2be42cd5ab4d335d076a1eb4627c41f5b340350
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166943"
---
# <a name="inline-assembler"></a>Assembleur inline

**Section spécifique à Microsoft**

Le langage assembleur atteint de nombreux objectifs, tels que l'amélioration de la vitesse du programme, la réduction des besoins en mémoire et le contrôle du matériel. Vous pouvez utiliser l'assembleur inline pour incorporer des instructions en langage assembleur directement dans vos programmes sources C et C++ sans code assembleur ni étapes de liaison supplémentaires. L'assembleur inline est intégré au compilateur. Par conséquent, vous n'avez pas besoin d'assembleur distinct tel que MASM (Microsoft Macro Assembler).

> [!NOTE]
>  Les programmes avec du code assembleur inline ne sont pas entièrement portables sur d'autres plateformes matérielles. Si vous concevez pour la portabilité, évitez d'utiliser l'assembleur inline.

L’assembly inline n’est pas pris en charge sur le ARM et x64 processeurs.  Les rubriques suivantes expliquent comment utiliser l'assembleur inline de Visual C/C++ avec des processeurs x86 :

- [Vue d’ensemble de l’assembleur inline](../../assembler/inline/inline-assembler-overview.md)

- [Avantages de l’assembly inline](../../assembler/inline/advantages-of-inline-assembly.md)

- [__asm](../../assembler/inline/asm.md)

- [Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)

- [Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)

- [Utilisation et conservation des registres dans un assembly inline](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)

- [Accès aux étiquettes dans l’assembly inline](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)

- [Appel des fonctions C dans l’assembly inline](../../assembler/inline/calling-c-functions-in-inline-assembly.md)

- [Appel des fonctions C++ dans l’assembly inline](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)

- [Définition des blocs __asm sous forme de macros C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)

- [Optimisation de l’assembly inline](../../assembler/inline/optimizing-inline-assembly.md)

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Fonctions intrinsèques du compilateur et langage assembleur](../../intrinsics/compiler-intrinsics-and-assembly-language.md)<br/>
[Informations de référence sur le langage C++](../../cpp/cpp-language-reference.md)<br/>