---
title: Spécificateurs de type C | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e37ac421627d4c4503d75eaf65188bbe234af015
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388381"
---
# <a name="c-type-specifiers"></a>Spécificateurs de type C

Les spécificateurs de type dans les déclarations définissent le type d'une variable ou d'une déclaration de fonction.

## <a name="syntax"></a>Syntaxe

*type-specifier* :  
&nbsp;&nbsp;**void**  
&nbsp;&nbsp;**char**  
&nbsp;&nbsp;**short**  
&nbsp;&nbsp;**int**  
&nbsp;&nbsp;**long**  
&nbsp;&nbsp;**float**  
&nbsp;&nbsp;**double**  
&nbsp;&nbsp;**signed**  
&nbsp;&nbsp;**unsigned**  
&nbsp;&nbsp;*struct-or-union-specifier*  
&nbsp;&nbsp;*enum-specifier*  
&nbsp;&nbsp;*typedef-name*  

Les types **signed char**, **signed int**, **signed short int** et **signed long int**, ainsi que leurs équivalents **unsigned** et **enum**, sont appelés types *intégraux*. Les spécificateurs de type **float**, **double** et **long double** sont appelés types *flottants* ou *à virgule flottante*. Vous pouvez utiliser n'importe quel spécificateur de type intégral ou à virgule flottante dans une variable ou une déclaration de fonction. Si aucun *type-specifier* n’est fourni dans une déclaration, **int** est utilisé par défaut.

Les mots clés facultatifs **signed** et **unsigned** peuvent précéder ou suivre tout type intégral, à l’exception **d’enum**, et peuvent également être utilisés seuls comme spécificateurs de type ; dans ce cas, ils sont compris respectivement comme **signed int** et **unsigned int**. S’il est utilisé seul, le mot clé **int** est supposé être **signed**. S’ils sont utilisés seuls, les mots clés **long** et **short** sont compris comme **long int** et **short int**.

Les types énumération sont considérés comme des types de base. Les spécificateurs de type pour les types énumération sont traités dans [Déclarations d'énumération](../c-language/c-enumeration-declarations.md).

Le mot clé **void** a trois utilisations : spécifier un type de retour de fonction, spécifier une liste de types d’arguments pour une fonction qui n’accepte pas d’argument et spécifier un pointeur vers un type non spécifié. Vous pouvez utiliser le type **void** pour déclarer des fonctions qui ne retournent aucune valeur ou pour déclarer un pointeur vers un type non spécifié. Pour plus d’informations sur **void** quand il apparaît seul entre les parenthèses qui suivent un nom de fonction, consultez [Arguments](../c-language/arguments.md).

**Section spécifique à Microsoft**

La vérification de type est maintenant conforme à la spécification ANSI, ce qui signifie que le type **short** et le type **int** sont des types distincts. Par exemple, voici une redéfinition dans le compilateur C Microsoft qui était acceptée par les versions précédentes du compilateur.

```C
int   myfunc();
short myfunc();
```

Cet exemple suivant génère également un avertissement concernant l'indirection vers différents types :

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Le compilateur C Microsoft génère également des avertissements pour les différences de signe. Exemple :

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Les expressions de type **void** sont évaluées quant à leurs effets secondaires. Vous ne pouvez en aucune manière utiliser la valeur (inexistante) d’une expression de type **void**, ni convertir une expression **void** (par conversion implicite ou explicite) en un type autre que **void**. Si vous utilisez une expression d’un autre type dans un contexte où une expression **void** est requise, sa valeur est ignorée.

Pour être conforme à la spécification ANSI, **void\*\*** ne peut pas être utilisé comme **int\*\***. Seul **void\*** peut être utilisé comme pointeur vers un type non spécifié.

**FIN de la section spécifique à Microsoft**

Vous pouvez créer des spécificateurs de type supplémentaires avec des déclarations **typedef**, comme décrit dans [Déclarations typedef](../c-language/typedef-declarations.md). Pour plus d'informations sur la taille de chaque type, consultez [Stockage des types de base](../c-language/storage-of-basic-types.md).

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)  
