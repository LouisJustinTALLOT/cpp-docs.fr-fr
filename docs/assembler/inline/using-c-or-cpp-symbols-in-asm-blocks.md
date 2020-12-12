---
description: 'En savoir plus sur : utilisation des symboles C ou C++ dans les blocs __asm'
title: Utilisation des symboles C ou C++ dans les blocs __asm
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: 3a2e46ab13bb316cb4761103d34da6c129c97995
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121886"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>Utilisation des symboles C ou C++ dans les blocs __asm

**Spécifique à Microsoft**

Un **`__asm`** bloc peut faire référence à n’importe quel symbole C ou C++ dans la portée où le bloc apparaît. (Les symboles C et C++ sont des noms de variables, des noms de fonctions et des étiquettes ; autrement dit, des noms qui ne sont pas des constantes symboliques ou des **`enum`** membres. Vous ne pouvez pas appeler les fonctions membres C++.)

Quelques restrictions s'appliquent à l'utilisation des symboles C et C++ :

- Chaque instruction en langage assembleur peut contenir un seul symbole C ou C++. Plusieurs symboles peuvent apparaître dans la même instruction d’assembly uniquement avec des expressions de **longueur**, de **type** et de **taille** .

- Les fonctions référencées dans un **`__asm`** bloc doivent être déclarées (prototypées) plus tôt dans le programme. Dans le cas contraire, le compilateur ne peut pas faire la distinction entre les noms de fonctions et les étiquettes du **`__asm`** bloc.

- Un **`__asm`** bloc ne peut pas utiliser de symboles C ou C++ avec la même orthographe que les mots réservés MASM (sans tenir compte de la casse). Les mots réservés MASM incluent des noms d’instructions tels que les noms **Push** et Register, comme si.

- Les balises de structure et d’Union ne sont pas reconnues dans les **`__asm`** blocs.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
