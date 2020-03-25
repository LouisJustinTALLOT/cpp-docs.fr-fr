---
title: Utilisation des symboles C ou C++ dans les blocs __asm
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: fd9f8b444d263818aca1b16260f70730d5350e7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169108"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>Utilisation des symboles C ou C++ dans les blocs __asm

**Section spécifique de Microsoft**

Un bloc `__asm` peut faire référence à n'importe quel symbole C ou C++ dans la portée où le bloc apparaît. (Les symboles C et C++ sont des noms de variables, des noms de fonctions et des étiquettes ; autrement dit, des noms qui ne sont pas des constantes symboliques ni des membres `enum`. Vous ne pouvez pas appeler les fonctions membres C++.)

Quelques restrictions s'appliquent à l'utilisation des symboles C et C++ :

- Chaque instruction en langage assembleur peut contenir un seul symbole C ou C++. Plusieurs symboles peuvent apparaître dans la même instruction d’assembly uniquement avec des expressions de **longueur**, de **type**et de **taille** .

- Les fonctions référencées dans un bloc `__asm` doivent être déclarées (prototypées) auparavant dans le programme. Sinon, le compilateur ne peut pas distinguer les noms de fonctions et les étiquettes dans le bloc `__asm`.

- Un bloc `__asm` ne peut utiliser aucun symbole C ou C++ avec la même orthographe que les mots réservés MASM (indépendamment de la casse). Les mots réservés MASM incluent des noms d’instructions tels que les noms **Push** et Register, comme si.

- Les étiquettes de structure et d’union ne sont pas reconnues dans les blocs `__asm`.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
