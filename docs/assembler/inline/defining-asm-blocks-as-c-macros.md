---
title: "Définition des blocs __asm en tant que Macros C | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af95f7b2c74d797203a0e6b3ddd6a92ddcb51e5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="defining-asm-blocks-as-c-macros"></a>Définition des blocs __asm sous forme de macros C
**Section spécifique à Microsoft**  
  
 Les macros C permettent d’insérer facilement le code assembleur dans votre code source, mais elles nécessitent un soin particulier, car une macro se développe en ligne logique unique. Pour créer des macros sans problème, respectez les règles suivantes :  
  
-   Mettez le bloc `__asm` entre accolades.  
  
-   Placez le mot clé `__asm` devant chaque instruction assembleur.  
  
-   Utilisez les anciens commentaires C (`/* comment */`) au lieu des commentaires de style assembly (`; comment`) ou des commentaires C sur une seule ligne (`// comment`).  
  
 À titre d'illustration, l'exemple suivant définit une macro simple :  
  
```  
#define PORTIO __asm      \  
/* Port output */         \  
{                         \  
   __asm mov al, 2        \  
   __asm mov dx, 0xD007   \  
   __asm out dx, al       \  
}  
```  
  
 À première vue, les trois derniers mots clés `__asm` semblent superflus. Ils sont toutefois nécessaires, car la macro se développe sur une seule ligne :  
  
```  
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }  
```  
  
 Le troisième et le quatrième mots clés `__asm` sont nécessaires en tant que séparateurs d'instruction. Les seuls séparateurs d'instruction reconnus dans les blocs `__asm` sont le caractère de saut de ligne et le mot clé `__asm`. Un bloc défini en tant que macro est une ligne logique unique. Vous devez donc séparer chaque instruction par `__asm`.  
  
 Les accolades sont également nécessaires. Si vous les omettez, le compilateur peut être perturbé par les instructions C ou C++ figurant sur la même ligne à droite de l'appel de macro. Sans l'accolade fermante, le compilateur ne peut pas indiquer où le code assembleur s'arrête. Il visualise les instructions C ou C++ figurant après le bloc `__asm` comme des instructions assembleur.  
  
 Les commentaires de style assembly qui commencent par un point-virgule (**;**) continuent jusqu'à la fin de la ligne. Cela pose des problèmes dans les macros, car le compilateur ignore tous les éléments figurant après le commentaire, jusqu'à la fin de la ligne logique. Il en est de même pour les commentaires C ou C++ sur une seule ligne (`// comment`). Pour empêcher les erreurs, utilisez les anciens commentaires C (`/* comment */`) dans les blocs `__asm` définis en tant que macros.  
  
 Un bloc `__asm` écrit en tant que macro C peut accepter des arguments. Cependant, contrairement à une macro C ordinaire, une macro `__asm` ne peut pas retourner de valeur. Ainsi, vous ne pouvez pas utiliser ce type de macros dans les expressions C ou C++.  
  
 Veillez à ne pas appeler les macros de ce type de façon arbitraire. Par exemple, appeler une macro en langage assembleur dans une fonction déclarée avec la convention `__fastcall` peut provoquer des résultats inattendus. (Consultez [utilisation et conservation des registres dans un Assembly Inline](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Assembleur inline](../../assembler/inline/inline-assembler.md)