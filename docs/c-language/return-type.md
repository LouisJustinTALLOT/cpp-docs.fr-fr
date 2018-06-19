---
title: Type de retour | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18d90604ccaebab2d3ed7812835c711d4d56995a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390185"
---
# <a name="return-type"></a>Type de retour
Le type de retour d’une fonction génère la taille et le type de la valeur retournée par la fonction et correspond au spécificateur de type dans la syntaxe ci-dessous :  
  
## <a name="syntax"></a>Syntaxe  
 *function-definition*:  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* est spécifique de Microsoft */  
  
 *declaration-specifiers* :  
 *storage-class-specifier declaration-specifiers* opt  
  
 *type-specifier declaration-specifiers* opt  
  
 *type-qualifier declaration-specifiers* opt  
  
 *type-specifier* :  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *typedef-name*  
  
 *type-specifier* peut spécifier tout type fondamental, structure ou union. Si vous n’incluez pas *type-specifier*, le type de retour `int` est supposé.  
  
 Le type de retour donné dans la définition de fonction doit correspondre au type de retour dans les déclarations de la fonction ailleurs dans le programme. Une fonction retourne une valeur lorsqu'une instruction `return` contenant une expression est exécutée. L'expression est évaluée, si nécessaire convertie vers le type de valeur de retour et retournée au point auquel la fonction a été appelée. Si une fonction est déclarée avec un type de retour `void`, une instruction return contenant une expression génère un avertissement et l'expression n'est pas évaluée.  
  
 Les exemples suivants illustrent des valeurs de retour de fonction.  
  
```  
typedef struct    
{  
    char name[20];  
    int id;  
    long class;  
} STUDENT;  
  
/* Return type is STUDENT: */  
  
STUDENT sortstu( STUDENT a, STUDENT b )  
{  
    return ( (a.id < b.id) ? a : b );  
}  
```  
  
 Cet exemple définit le type `STUDENT` avec une déclaration `typedef` et définit la fonction `sortstu` pour obtenir le type de retour `STUDENT`. La fonction sélectionne et retourne un de ses arguments de structure. Dans les appels suivants à la fonction, le compilateur effectue une vérification pour s'assurer que les types d'argument sont `STUDENT`.  
  
> [!NOTE]
>  L'efficacité est améliorée en passant des pointeurs à la structure plutôt qu'à la structure entière.  
  
```  
char *smallstr( char s1[], char s2[] )  
{  
    int i;  
  
    i = 0;  
    while ( s1[i] != '\0' && s2[i] != '\0' )  
        i++;  
    if ( s1[i] == '\0' )  
        return ( s1 );  
    else  
        return ( s2 );  
}  
```  
  
 Cet exemple définit une fonction qui retourne un pointeur vers un tableau de caractères. La fonction accepte deux tableaux de caractères (chaînes) comme arguments et retourne un pointeur vers la plus courte des deux chaînes. Un pointeur vers un tableau pointe vers le premier des éléments du tableau et a son type. Par conséquent, le type de retour de la fonction est un pointeur vers le type `char`.  
  
 Vous n'avez pas besoin de déclarer des fonctions avec le type de retour `int` avant de les appeler bien que les prototypes soient recommandés afin d'autoriser une vérification de type correcte pour les arguments et les valeurs de retour.  
  
## <a name="see-also"></a>Voir aussi  
 [Définitions de fonction C](../c-language/c-function-definitions.md)