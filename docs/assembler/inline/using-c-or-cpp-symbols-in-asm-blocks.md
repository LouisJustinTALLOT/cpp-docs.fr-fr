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
ms.openlocfilehash: fc22af8ec04d616eb8f5566b118e19c405605401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552514"
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>Utilisation des symboles C ou C++ dans les blocs __asm

**Section spécifique à Microsoft**

Un bloc `__asm` peut faire référence à n'importe quel symbole C ou C++ dans la portée où le bloc apparaît. (Les symboles C et C++ sont des noms de variables, des noms de fonctions et des étiquettes ; autrement dit, des noms qui ne sont pas des constantes symboliques ni des membres `enum`. Vous ne pouvez pas appeler les fonctions membres C++.)

Quelques restrictions s'appliquent à l'utilisation des symboles C et C++ :

- Chaque instruction en langage assembleur peut contenir un seul symbole C ou C++. Plusieurs symboles peuvent apparaître dans la même instruction assembleur uniquement avec **longueur**, **TYPE**, et **taille** expressions.

- Les fonctions référencées dans un bloc `__asm` doivent être déclarées (prototypées) auparavant dans le programme. Sinon, le compilateur ne peut pas distinguer les noms de fonctions et les étiquettes dans le bloc `__asm`.

- Un bloc `__asm` ne peut utiliser aucun symbole C ou C++ avec la même orthographe que les mots réservés MASM (indépendamment de la casse). Mots réservés MASM incluent des noms d’instructions comme **PUSH** et inscrire les noms, tels que SI.

- Les étiquettes de structure et d’union ne sont pas reconnues dans les blocs `__asm`.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>