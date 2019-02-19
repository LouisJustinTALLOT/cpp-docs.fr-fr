---
title: for, instruction (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: df00bcab2f9f9e51a6f37e19670b6cd240fa5cc4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152831"
---
# <a name="for-statement-c"></a>for, instruction (C)

L’instruction **for** vous permet de répéter une instruction, ou une instruction composée, un nombre de fois spécifié. Le corps d’une instruction **for** est exécuté zéro ou plusieurs fois jusqu’à ce qu’une condition facultative ait la valeur false. Vous pouvez utiliser des expressions facultatives dans l’instruction **for** pour initialiser et modifier des valeurs pendant l’exécution de l’instruction **for**.

## <a name="syntax"></a>Syntaxe

*itération-instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*

L’exécution d’une instruction **for** continue comme suit :

1. *init-expression* est évaluée (s’il en existe une). Cela spécifie l'initialisation de la boucle. Il n’existe aucune restriction concernant le type d’*init-expression*.

1. *cond-expression* est évaluée (s’il en existe une). Cette expression doit avoir un type arithmétique ou pointeur. Elle est évaluée avant chaque itération. Trois résultats sont possibles :

   - Si *cond-expression* est **true** (différente de zéro), *statement* est exécuté ; puis *loop-expression* est évaluée (s’il en existe une). *loop-expression* est évaluée à l’issue de chaque itération. Il n'existe aucune restriction sur son type. Les effets secondaires s'exécuteront dans l'ordre. Le processus recommence ensuite avec l’évaluation de *cond-expression*.

   - Si *cond-expression* est omis, *cond-expression* est considéré comme true, et l’exécution reprend exactement comme décrit dans le paragraphe précédent. Une instruction **for** sans argument *cond-expression* se termine uniquement lorsqu’une instruction **break** ou **return** dans le corps d’instruction est exécutée ou lorsqu’une instruction **goto** (vers une instruction étiquetée extérieure au corps d’instruction **for**) est exécutée.

   - Si l’élément *cond-expression* est **false** (0), l’instruction **for** se termine et le contrôle passe à l’instruction suivante du programme.

L’instruction **for** peut également se terminer lorsqu’une instruction **break**, **goto** ou **return** est exécutée dans le corps de l’instruction. Une instruction **continue** dans une boucle **for** entraîne l’évaluation d’une boucle *loop-expression*. Lorsqu’une instruction **break** est exécutée dans une boucle **for**, *loop-expression* n’est ni évalué, ni exécuté. Cette instruction

```C
for( ; ; )
```

est la méthode courante pour produire une boucle infinie qui ne peut être quittée qu’avec une instruction **break**, **goto** ou **return**.

## <a name="example"></a>Exemple

L’exemple suivant illustre l’instruction **for** :

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>Sortie

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
