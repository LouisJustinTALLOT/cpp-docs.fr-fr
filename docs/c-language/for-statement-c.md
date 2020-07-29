---
title: for, instruction (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: 91675fbe15ec6abf5aae4548990d9b4e0703e967
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229725"
---
# <a name="for-statement-c"></a>for, instruction (C)

L' **`for`** instruction vous permet de répéter une instruction ou une instruction composée un nombre de fois spécifié. Le corps d’une **`for`** instruction est exécuté zéro ou plusieurs fois jusqu’à ce qu’une condition facultative devienne false. Vous pouvez utiliser des expressions facultatives dans l' **`for`** instruction pour initialiser et modifier des valeurs pendant l' **`for`** exécution de l’instruction.

## <a name="syntax"></a>Syntaxe

*itération-instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`for`****(** *init-expression*<sub>OPT</sub> **;** *cond-expression*<sub>OPT</sub> **;** *loop-expression*<sub>OPT</sub> **)** ( *instruction* )

L’exécution d’une **`for`** instruction continue comme suit :

1. *init-expression* est évaluée (s’il en existe une). Cela spécifie l'initialisation de la boucle. Il n’existe aucune restriction concernant le type d’*init-expression*.

1. *cond-expression* est évaluée (s’il en existe une). Cette expression doit avoir un type arithmétique ou pointeur. Elle est évaluée avant chaque itération. Trois résultats sont possibles :

   - Si *cond-expression* est **`true`** (différent de zéro), l' *instruction* est exécutée, puis *loop-expression, le*cas échéant, est évaluée. *loop-expression* est évaluée à l’issue de chaque itération. Il n'existe aucune restriction sur son type. Les effets secondaires s'exécuteront dans l'ordre. Le processus recommence ensuite avec l’évaluation de *cond-expression*.

   - Si *cond-expression* est omis, *cond-expression* est considéré comme true, et l’exécution reprend exactement comme décrit dans le paragraphe précédent. Une **`for`** instruction sans argument *cond-expression* se termine uniquement lorsqu’une **`break`** **`return`** instruction ou dans le corps de l’instruction est exécutée ou lorsqu’une instruction **`goto`** (vers une instruction étiquetée en dehors du corps de l' **`for`** instruction) est exécutée.

   - Si *cond-expression* a **`false`** la valeur (0), l’exécution de l' **`for`** instruction se termine et le contrôle passe à l’instruction suivante dans le programme.

Une **`for`** instruction se termine également lorsqu' **`break`** une **`goto`** instruction, ou **`return`** dans le corps de l’instruction est exécutée. Une **`continue`** instruction dans une **`for`** boucle entraîne l’évaluation de *loop-expression* . Lorsqu’une **`break`** instruction est exécutée à l’intérieur d’une **`for`** boucle, *loop-expression* n’est pas évaluée ou exécutée. Cette instruction

```C
for( ; ; )
```

est la méthode personnalisée pour produire une boucle infinie qui ne peut être quittée qu’avec une **`break`** **`goto`** instruction, ou **`return`** .

## <a name="example"></a>Exemple

Cet exemple illustre l' **`for`** instruction :

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

## <a name="output"></a>Output

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
