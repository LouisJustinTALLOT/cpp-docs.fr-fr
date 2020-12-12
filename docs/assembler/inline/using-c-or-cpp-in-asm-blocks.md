---
description: 'En savoir plus sur : utilisation de C ou C++ dans les blocs __asm'
title: Utilisation de C ou C++ dans les blocs __asm
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
ms.openlocfilehash: 2fc1987339fcbabee07e2b626c3ae764c3d5e2e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121925"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>Utilisation de C ou C++ dans les blocs __asm

**Spécifique à Microsoft**

Étant donné que les instructions d'assembly inline peuvent être combinées avec des instructions C ou C++, elles peuvent faire référence à des variables C ou C++ par nom et utiliser de nombreux autres éléments de ces langages.

Un **`__asm`** bloc peut utiliser les éléments de langage suivants :

- Symboles, notamment les étiquettes et les noms de variable et de fonction

- Constantes, y compris les constantes symboliques et **`enum`** les membres

- Macros et directives de préprocesseur

- __/ \* Commentaires \* ( /__ et __//__ )

- Noms de types (partout où un type MASM est autorisé)

- **`typedef`** noms, généralement utilisés avec des opérateurs tels que **ptr** et **type** , ou pour spécifier des membres de structure ou d’Union

Dans un **`__asm`** bloc, vous pouvez spécifier des constantes entières avec la notation C ou l’assembleur de base (0x100 et 100h sont équivalents, par exemple). Cela vous permet de définir (avec `#define`) une constante en C puis de l'utiliser dans C ou C++ et dans des parties d'assembly du programme. Vous pouvez également spécifier des constantes au format octal en les faisant précéder d'un 0. Par exemple, 0777 spécifie une constante octale.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Utilisation d’opérateurs dans les blocs __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Utilisation de symboles C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Accès aux données C ou C++ dans les blocs __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Écriture de fonctions avec un assembly inline](../../assembler/inline/writing-functions-with-inline-assembly.md)

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
