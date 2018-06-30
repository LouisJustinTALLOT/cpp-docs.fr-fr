---
title: À l’aide de C ou C++ dans les blocs __asm | Documents Microsoft
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96ed46cdf44ccacee806dd03bf7eacca26eec32d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120942"
---
# <a name="using-c-or-c-in-asm-blocks"></a>Utilisation de C ou C++ dans les blocs __asm

** Spécifique à Microsoft **

Étant donné que les instructions d'assembly inline peuvent être combinées avec des instructions C ou C++, elles peuvent faire référence à des variables C ou C++ par nom et utiliser de nombreux autres éléments de ces langages.

Un bloc `__asm` peut utiliser les éléments de langage suivants :

- Symboles, notamment les étiquettes et les noms de variable et de fonction

- Constantes, notamment les constantes symboliques et les membres `enum`

- Macros et directives de préprocesseur

- Commentaires (les deux __/ \* \* /__ et __//__ )

- Noms de types (partout où un type MASM est autorisé)

- `typedef` généralement utilisées avec des opérateurs tels que les noms **PTR** et **TYPE** ou pour spécifier les membres de structure ou union

Dans un bloc `__asm`, vous pouvez spécifier des constantes entières avec la notation C ou la notation de base de l'assembleur (0x100 et 100h sont équivalents, par exemple). Cela vous permet de définir (avec `#define`) une constante en C puis de l'utiliser dans C ou C++ et dans des parties d'assembly du programme. Vous pouvez également spécifier des constantes au format octal en les faisant précéder d'un 0. Par exemple, 0777 spécifie une constante octale.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Utilisation d’opérateurs dans les blocs __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [À l’aide de C ou C++ symboles les blocs __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Accès aux données C ou C++ dans les blocs __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Écriture de fonctions avec un assembly inline](../../assembler/inline/writing-functions-with-inline-assembly.md)

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)
