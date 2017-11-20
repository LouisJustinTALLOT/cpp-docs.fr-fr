---
title: "Opérateurs relationnels et d'égalité C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b1581fe5a952d1ea8e78f29e606af5ac148f3b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="c-relational-and-equality-operators"></a>Opérateurs relationnels et d'égalité C
Les opérateurs binaires relationnels et d’égalité comparent leur premier opérande à leur second opérande pour tester la validité de la relation spécifiée. Le résultat d'une expression relationnelle est 1 si la relation testée a la valeur true et 0 si elle a la valeur false. Le type du résultat est `int`.  
  
 **Syntaxe**  
  
 *relational-expression* :  
 *shift-expression*  
  
 *relational-expression*  **\<**  *shift-expression*  
  
 *relational-expression*  **>**  *shift-expression*  
  
 *relational-expression*  **\<=**  *shift-expression*  
  
 *relational-expression*  **>=**  *shift-expression*  
  
 *equality-expression* :  
 *relational-expression*  
  
 *equality-expression*  **==**  *relational-expression*  
  
 *equality-expression*  **!=**  *relational-expression*  
  
 Les opérateurs relationnels et d'égalité testent les relations suivantes :  
  
|Opérateur|Relation testée|  
|--------------|-------------------------|  
|**\<**|Premier opérande inférieur au second opérande|  
|**>**|Premier opérande supérieur au second opérande|  
|**\<=**|Premier opérande inférieur ou égal au second opérande|  
|**>=**|Premier opérande supérieur ou égal au second opérande|  
|`==`|Premier opérande égal au second opérande|  
|`!=`|Premier opérande différent du second opérande|  
  
 Les quatre premiers opérateurs dans la liste ci-dessus ont une priorité plus élevée que les opérateurs d'égalité (`==` et `!=`). Consultez les informations de priorité dans la table [Priorité et associativité des opérateurs C](../c-language/precedence-and-order-of-evaluation.md).  
  
 Les opérandes peuvent être de type intégral, flottant ou pointeur. Les types d'opérande peuvent être différents. Les opérateurs relationnels exécutent les conversions arithmétiques habituelles sur les opérandes de type intégral et flottant. En outre, vous pouvez utiliser les combinaisons suivantes des types d'opérande avec les opérateurs relationnels et d'égalité :  
  
-   Les deux opérandes de tout opérateur relationnel ou d'égalité peuvent être des pointeurs vers le même type. Pour les opérateurs d'égalité (`==`) et d'inégalité (`!=`), le résultat de la comparaison indique si les deux pointeurs pointent vers le même emplacement de mémoire. Pour les autres opérateurs relationnels (**\<**, **>**, **\<**= et **>**=), le résultat de la comparaison indique la position relative des deux adresses mémoire des objets vers lesquels le pointage est effectué. Les opérateurs relationnels comparent uniquement les décalages.  
  
     La comparaison de pointeur est définie uniquement pour les parties du même objet. Si les pointeurs font référence aux membres d'un tableau, la comparaison est équivalente à la comparaison des indices correspondants. L'adresse du premier élément du tableau est « inférieure à » l'adresse du dernier élément. Dans le cas de structures, les pointeurs vers des membres de structures déclarés ultérieurement sont « supérieurs à » aux pointeurs vers des membres déclarés précédemment dans la structure. Les pointeurs vers des membres de la même union sont égaux.  
  
-   Une valeur de pointeur peut être comparée à la valeur de constante 0 pour l'égalité (`==`) ou l'inégalité (`!=`). Un pointeur avec une valeur de 0 est appelé pointeur « Null » ; autrement dit, il ne pointe pas vers un emplacement de mémoire valide.  
  
-   Les opérateurs d'égalité suivent les mêmes règles que les opérateurs relationnels, mais offrent des possibilités supplémentaires : un pointeur peut être comparé à une expression intégrale constante ayant pour valeur 0, ou à un pointeur vers `void`. Si deux pointeurs sont tous deux des pointeurs Null, ils sont considérés comme égaux. Les opérateurs d'égalité comparent à la fois le segment et le décalage.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent des opérateurs relationnels et d'égalité.  
  
```  
int x = 0, y = 0;  
if ( x < y )  
```  
  
 Étant donné que `x` et `y` sont égaux, l'expression dans cet exemple génère la valeur 0.  
  
```  
char array[10];  
char *p;  
  
for ( p = array; p < &array[10]; p++ )  
    *p = '\0';  
```  
  
 Le fragment dans cet exemple affecte à chaque élément d'`array` une constante caractère Null.  
  
```  
enum color { red, white, green } col;  
   .  
   .  
   .  
   if ( col == red )  
   .  
   .  
   .  
```  
  
 Ces instructions déclarent une variable d'énumération nommée `col` avec la balise `color`. À tout moment, la variable peut contenir une valeur entière 0, 1 ou 2, qui représente un des éléments de l'ensemble d'énumération `color` : le rouge, le blanc ou le vert, respectivement. Si `col` contient 0 lorsque l'instruction **if** est exécutée, toutes les instructions dépendant de **if** sont exécutées.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs relationnels : \<, >, \<= et >=](../cpp/relational-operators-equal-and-equal.md)   
 [Opérateurs d’égalité : == et !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)