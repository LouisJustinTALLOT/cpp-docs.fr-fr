---
description: 'En savoir plus sur : définition des blocs de __asm en tant que macros C'
title: Définition des blocs __asm sous forme de macros C
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: a0fe13acdd5a75fd86fd8107396632a5c6e7c283
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117835"
---
# <a name="defining-__asm-blocks-as-c-macros"></a>Définition des blocs __asm sous forme de macros C

**Spécifique à Microsoft**

Les macros C permettent d'insérer facilement le code assembleur dans votre code source, mais elles nécessitent un soin particulier, car une macro se développe en ligne logique unique. Pour créer des macros sans problème, respectez les règles suivantes :

- Placez le **`__asm`** bloc entre accolades.

- Placez le **`__asm`** mot clé devant chaque instruction d’assembly.

- Utilisez les anciens commentaires C (`/* comment */`) au lieu des commentaires de style assembly (`; comment`) ou des commentaires C sur une seule ligne (`// comment`).

À titre d'illustration, l'exemple suivant définit une macro simple :

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

À première vue, les trois derniers **`__asm`** Mots-clés semblent superflus. Ils sont toutefois nécessaires, car la macro se développe sur une seule ligne :

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

Les troisième et quatrième **`__asm`** Mots clés sont nécessaires en tant que séparateurs d’instructions. Les seuls séparateurs d’instructions reconnus dans **`__asm`** les blocs sont le caractère de saut de ligne et le **`__asm`** mot clé. Étant donné qu’un bloc défini en tant que macro est une ligne logique, vous devez séparer chaque instruction par **`__asm`** .

Les accolades sont également nécessaires. Si vous les omettez, le compilateur peut être perturbé par les instructions C ou C++ figurant sur la même ligne à droite de l'appel de macro. Sans l’accolade fermante, le compilateur ne peut pas indiquer où le code assembleur s’arrête et il voit les instructions C ou C++ après le **`__asm`** bloc en tant qu’instructions d’assembly.

Les commentaires de style assembly qui commencent par un point-virgule (**;**) continuent jusqu’à la fin de la ligne. Cela pose des problèmes dans les macros, car le compilateur ignore tous les éléments figurant après le commentaire, jusqu'à la fin de la ligne logique. Il en est de même pour les commentaires C ou C++ sur une seule ligne (`// comment`). Pour éviter les erreurs, utilisez les anciens commentaires C ( `/* comment */` ) dans **`__asm`** les blocs définis en tant que macros.

Un **`__asm`** bloc écrit sous la forme d’une macro C peut accepter des arguments. Toutefois, contrairement à une macro C ordinaire, une **`__asm`** macro ne peut pas retourner de valeur. Ainsi, vous ne pouvez pas utiliser ce type de macros dans les expressions C ou C++.

Veillez à ne pas appeler les macros de ce type de façon arbitraire. Par exemple, l’appel d’une macro en langage assembleur dans une fonction déclarée avec la **`__fastcall`** Convention peut provoquer des résultats inattendus. (Consultez [utilisation et préservation des registres dans un assembly inline](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
