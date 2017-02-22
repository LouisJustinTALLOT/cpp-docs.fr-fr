---
title: "D&#233;clarations de tableau | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tableaux (C++), déclarer"
  - "déclarer des tableaux"
  - "tableaux multidimensionnels"
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# D&#233;clarations de tableau
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Une « déclaration de tableau » nomme le tableau et spécifie le type de ses éléments.  Elle peut également définir le nombre d'éléments du tableau.  Une variable de type tableau est considérée comme un pointeur vers le type des éléments du tableau.  
  
## Syntaxe  
 `declaration`:  
 *declaration\-specifiers init\-declarator\-list*  opt               **;**  
  
 *init\-declarator\-list* :  
 *init\-declarator*  
  
 *init\-declarator\-list* **,**  *init\-declarator*  
  
 *init\-declarator* :  
 *declarator*  
  
 *declarator*  **\=**  *initializer*  
  
 `declarator`:  
 *pointer*  opt *direct\-declarator*  
  
 *direct\-declarator* :  
 *direct\-declarator*  **\[**  *constant\-expression*  opt **\]**  
  
 Étant donné que *constant\-expression* est facultatif, la syntaxe a deux formes :  
  
-   La première forme définit une variable tableau.  L'argument *constant\-expression* entre crochets spécifie le nombre d'éléments du tableau.  Si *constant\-expression* est présent, il doit être de type intégral et sa valeur doit être supérieure à zéro.  Le type de chaque élément est donné par *type\-specifier*. Il peut s'agir de n'importe quel type, à l'exception de `void`.  Un élément de tableau ne peut pas être un type de fonction.  
  
-   La deuxième forme déclare une variable définie ailleurs.  L'argument *constant\-expression* entre crochets est omis, mais pas les crochets.  Vous pouvez utiliser cette forme uniquement si vous avez précédemment initialisé le tableau, si vous l'avez déclaré comme paramètre ou si vous l'avez déclaré comme référence à un tableau explicitement défini ailleurs dans le programme.  
  
 Dans les deux formes, *direct\-declarator* nomme la variable et peut modifier le type de la variable.  Les crochets \(**\[ \]**\) qui suivent *direct\-declarator* modifient le déclarateur en type tableau.  
  
 Des qualificateurs de type peuvent apparaître dans la déclaration d'un objet de type tableau, mais les qualificateurs s'appliquent aux éléments plutôt qu'au tableau lui\-même.  
  
 Vous pouvez déclarer un tableau de tableaux \(tableau « multidimensionnel »\) en indiquant après le déclarateur de tableau une liste d'expressions constantes entre crochets, comme illustré ici :  
  
```  
  
type-specifier declarator [constant-expression] [constant-expression] ...  
```  
  
 Chaque *constant\-expression* entre crochets définit le nombre d'éléments d'une dimension donnée : les tableaux à deux dimensions comportent deux expressions entre crochets, les tableaux à trois dimensions en comportent trois, et ainsi de suite.  Vous pouvez omettre la première expression constante si vous avez initialisé le tableau, si vous l'avez déclaré comme paramètre ou si vous l'avez déclaré comme référence à un tableau explicitement défini ailleurs dans le programme.  
  
 Vous pouvez définir des tableaux de pointeurs en différents types d'objets en utilisant des déclarateurs complexes, comme décrit dans la section [Interprétation de déclarateurs plus complexes](../c-language/interpreting-more-complex-declarators.md).  
  
 Les tableaux sont stockés par ligne.  Par exemple, le tableau suivant comprend deux lignes comportant chacune trois colonnes :  
  
```  
char A[2][3];  
```  
  
 Les trois colonnes de la première ligne sont stockées en premier, suivies des trois colonnes de la deuxième ligne.  Cela signifie que le dernier indice varie plus rapidement.  
  
 Pour faire référence à un élément individuel d'un tableau, utilisez une expression d'indice, comme décrit dans la section [Opérateurs suffixés](../c-language/postfix-operators.md).  
  
## Exemples  
 Les exemples suivants illustrent des déclarations de tableau :  
  
```  
float matrix[10][15];  
```  
  
 Le tableau à deux dimensions nommé `matrix` possède 150 éléments. Chaque élément est de type **float**.  
  
```  
struct {  
    float x, y;  
} complex[100];  
```  
  
 Il s'agit d'une déclaration d'un tableau de structures.  Ce tableau contient 100 éléments. Chaque élément est une structure contenant deux membres.  
  
```  
extern char *name[];  
```  
  
 Cette instruction déclare le type et le nom d'un tableau de pointeurs vers `char`.  La définition réelle de `name` se produit ailleurs.  
  
 **Section spécifique à Microsoft**  
  
 Le type d'entier requis pour conserver la taille maximale d'un tableau est la taille de **size\_t**.  Défini dans le fichier d'en\-tête STDDEF.H, **size\_t** est un `unsigned int` présentant la plage de 0x00000000 à 0x7CFFFFFF.  
  
 **FIN de la section spécifique à Microsoft**  
  
## Voir aussi  
 [Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)