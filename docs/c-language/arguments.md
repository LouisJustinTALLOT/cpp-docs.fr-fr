---
title: Arguments | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48e8952d6f25d737a72733899e51387fed65e8a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387159"
---
# <a name="arguments"></a>Arguments
Les arguments figurant dans un appel de fonction ont la forme suivante :  
  
```  
  
expression  
(  
expression-list <SUB>opt</SUB> )  /* Function call */  
```  
  
 Dans un appel de fonction, *expression-list* est une liste d'expressions (séparées par des virgules). Les valeurs de ces dernières expressions sont les arguments passés à la fonction. Si la fonction n’accepte aucun argument, *expression-list* doit contenir le mot clé `void`.  
  
 Un argument peut être une valeur quelconque dotée du type fondamental, structure, union ou pointeur. Tous les arguments sont passés par valeur. Cela signifie qu'une copie de l'argument est assignée au paramètre correspondant. La fonction ne connaît pas l'emplacement mémoire réel de l'argument passé. La fonction utilise cette copie sans affecter la variable de laquelle elle était initialement dérivée.  
  
 Vous ne pouvez pas passer des tableaux ni des fonctions en tant qu'arguments, mais vous pouvez passer des pointeurs désignant ces éléments. Les pointeurs fournissent un moyen à une fonction d'accéder à une valeur par référence. Comme un pointeur vers une variable contient l'adresse de la variable, la fonction peut utiliser cette adresse pour accéder à la valeur de la variable. Les arguments de pointeur permettent à une fonction d'accéder aux tableaux et aux fonctions, même si les tableaux et les fonctions ne peuvent pas être passés en tant qu'arguments.  
  
 L'ordre dans lequel les arguments sont évalués peut varier selon les différents compilateurs et niveaux d'optimisation. Toutefois, les arguments et tous les effets secondaires sont complètement évalués avant que la fonction soit entrée. Consultez [Effets secondaires](../c-language/side-effects.md) pour obtenir des informations sur les effets secondaires.  
  
 L’argument *expression-list* dans un appel de fonction est évalué et les conversions arithmétiques habituelles sont effectuées sur chaque argument dans l’appel de fonction. Si un prototype est disponible, le type d’argument résultant est comparé au paramètre correspondant du prototype. S'ils ne correspondent pas, une conversion est exécutée ou un message de diagnostic est publié. Les paramètres subissent également les conversions arithmétiques habituelles.  
  
 Le nombre d’expressions dans *expression-list* doit correspondre au nombre de paramètres, à moins que le prototype ou la définition de la fonction spécifie explicitement un nombre variable d’arguments. Dans ce cas, le compilateur vérifie autant d’arguments qu’il existe de noms de types dans la liste des paramètres, et les convertit si nécessaire, comme décrit ci-dessus. Consultez [Appels avec un nombre variable d’arguments](../c-language/calls-with-a-variable-number-of-arguments.md) pour plus d’informations.  
  
 Si la liste de paramètres du prototype contient uniquement le mot clé `void`, le compilateur attend zéro argument dans l'appel de fonction et zéro paramètre dans la définition. Un message de diagnostic est publié si des arguments sont détectés.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous utilise des pointeurs comme arguments :  
  
```  
int main()  
{  
    /* Function prototype */  
  
    void swap( int *num1, int *num2 );  
    int x, y;  
    .  
    .  
    .  
    swap( &x, &y );  /* Function call */  
}  
  
/* Function definition */  
  
void swap( int *num1, int *num2 )  
{  
    int t;  
  
    t = *num1;  
    *num1 = *num2;  
    *num2 = t;  
}  
```  
  
 Dans cet exemple, la fonction `swap` est déclarée dans `main` de manière à posséder deux arguments, représentés respectivement par les identificateurs `num1` et `num2`, qui sont tous les deux des pointeurs désignant des valeurs `int`. Les paramètres `num1` et `num2` dans la définition de style du prototype sont également déclarés comme pointeurs désignant des valeurs de type `int`.  
  
 Dans l'appel de fonction  
  
```  
swap( &x, &y )  
```  
  
 l'adresse de `x` est stockée dans `num1` et l'adresse de `y` est stockée dans `num2`. À présent, deux noms, ou « alias », existent pour le même emplacement. Les références à `*num1` et `*num2` dans `swap` sont effectivement des références à `x` et `y` dans `main`. Les assignations dans `swap` échangent en fait les contenus de `x` et `y`. Par conséquent, aucune instruction `return` n'est requise.  
  
 Le compilateur effectue la vérification des types sur les arguments passés à `swap` car le prototype de `swap` inclut des types d'argument pour chaque paramètre. Les identificateurs placés entre les parenthèses du prototype et de la définition peuvent être identiques ou différents. L’essentiel est que les types des arguments correspondent à ceux des listes de paramètres, dans le prototype et la définition.  
  
## <a name="see-also"></a>Voir aussi  
 [Appels de fonction](../c-language/function-calls.md)