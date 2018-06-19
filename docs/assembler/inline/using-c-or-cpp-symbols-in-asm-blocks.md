---
title: À l’aide de symboles C ou C++ dans les blocs __asm | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746614de653649747bf20ae4c223e5687ee53f5c
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049425"
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>Utilisation des symboles C ou C++ dans les blocs __asm
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Un bloc `__asm` peut faire référence à n'importe quel symbole C ou C++ dans la portée où le bloc apparaît. (Les symboles C et C++ sont des noms de variables, des noms de fonctions et des étiquettes ; autrement dit, des noms qui ne sont pas des constantes symboliques ni des membres `enum`. Vous ne pouvez pas appeler les fonctions membres C++.)  
  
 Quelques restrictions s'appliquent à l'utilisation des symboles C et C++ :  
  
-   Chaque instruction en langage assembleur peut contenir un seul symbole C ou C++. Plusieurs symboles peuvent apparaître dans la même instruction assembleur uniquement avec **longueur**, **TYPE**, et **taille** expressions.  
  
-   Les fonctions référencées dans un bloc `__asm` doivent être déclarées (prototypées) auparavant dans le programme. Sinon, le compilateur ne peut pas distinguer les noms de fonctions et les étiquettes dans le bloc `__asm`.  
  
-   Un bloc `__asm` ne peut utiliser aucun symbole C ou C++ avec la même orthographe que les mots réservés MASM (indépendamment de la casse). Mots réservés MASM incluent les noms d’instructions, tels que **PUSH** et inscrire des noms, tels que SI.  
  
-   Les balises de structure et d'union ne sont pas reconnues dans les blocs `__asm`.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)