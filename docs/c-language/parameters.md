---
title: "Param&#232;tres | Microsoft Docs"
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
  - "points de suspension ..."
  - "arguments (C++), function (fonction)"
  - "points de suspension (...), paramètres"
  - "arguments de fonction, différences par rapport aux paramètres"
  - "paramètres de fonction"
  - "paramètres de fonction, syntaxe"
  - "fonctions (C), paramètres"
  - "paramètres (C++)"
  - "paramètres (C++), function (fonction)"
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Param&#232;tres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Les arguments sont les noms des valeurs passées à une fonction par un appel de fonction.  Les paramètres sont les valeurs que la fonction compte recevoir.  Dans un prototype de fonction, les parenthèses suivant le nom de la fonction contiennent une liste complète des types et des paramètres de la fonction.  Les déclarations de paramètres spécifient les types, les tailles et les identificateurs des valeurs stockées dans les paramètres.  
  
## Syntaxe  
 *function\-definition* :  
 *declaration\-specifiers*  opt *attribute\-seq* opt *declarator declaration\-list* opt *compound\-statement*  
  
 \/\* *attribute\-seq* est spécifique à Microsoft \*\/  
  
 *declarator*  :  
 *pointer*  opt *direct\-declarator*  
  
 *direct\-declarator* :\/\* Déclarateur de fonction \*\/  
 *direct\-declarator*  **\(**  *parameter\-type\-list*  **\)**  \/\* Déclarateur de nouveau style \*\/  
  
 *parameter\-type\-list* : \/\* Liste de paramètres \*\/  
 *parameter\-list*  
  
 *parameter\-list*  **,...**  
  
 *parameter\-list* :  
 *parameter\-declaration*  
  
 *parameter\-list*  **,**  *parameter\-declaration*  
  
 *parameter\-declaration* :  
 *declaration\-specifiers declarator*  
  
 *declaration\-specifiers abstract\-declarator*  opt  
  
 *parameter\-type\-list* est une séquence de déclarations de paramètre séparée par des virgules.  La formule de chaque paramètre dans la liste des paramètres ressemble à ceci :  
  
```  
[register]  type-specifier [declarator]   
```  
  
 Les paramètres de fonction déclarés avec l'attribut **auto** génèrent des erreurs.  Les identificateurs des paramètres sont utilisés dans le corps de la fonction pour faire référence aux valeurs passées à la fonction.  Vous pouvez nommer les paramètres dans un prototype, mais les noms sont hors de portée à la fin de la déclaration.  Par conséquent, des noms de paramètres peuvent être assignés de la même façon ou différemment dans la définition de fonction.  Ces identificateurs ne peuvent pas être redéfinis dans le bloc extérieur du corps de la fonction, mais ils peuvent être redéfinis dans les blocs internes et imbriqués comme si la liste des paramètres était un bloc englobant.  
  
 Chaque identificateur figurant dans *parameter\-type\-list* doit être précédé par son spécificateur de type approprié, comme illustré dans cet exemple :  
  
```  
void new( double x, double y, double z )  
{  
    /* Function body here */  
}  
```  
  
 Si au moins un paramètre apparaît dans la liste des paramètres, cette liste peut se terminer par une virgule suivie de trois points \(**, ...**\).  Cette construction, appelée « notation de sélection », indique un nombre variable d'arguments à la fonction. \(Consultez [Appels avec un nombre variable d'arguments](../c-language/calls-with-a-variable-number-of-arguments.md) pour plus d'informations.\) Toutefois, un appel à la fonction doit posséder autant d'arguments car il existe des paramètres avant la dernière virgule.  
  
 Si aucun argument ne doit être passé à la fonction, la liste des paramètres est remplacée par le mot clé `void`.  Cette utilisation de `void` est distincte de son utilisation comme un spécificateur de type.  
  
 L'ordre et le type des paramètres, y compris toute utilisation de la notation de sélection, doivent être identiques dans toutes les déclarations de fonctions \(le cas échéant\) et dans la définition de fonction.  Les types des arguments après les conversions arithmétiques habituelles doivent être compatibles\-assignation avec les types de paramètres correspondants. \(Consultez [Conversions arithmétiques habituelles](../c-language/usual-arithmetic-conversions.md) pour plus d'informations sur les conversions arithmétiques.\) Les arguments suivant les points de suspension ne sont pas activés.  Un paramètre peut avoir n'importe quel type fondamental, structure, union, pointeur ou tableau.  
  
 Le compilateur effectue les conversions arithmétiques habituelles indépendamment sur chaque paramètre et sur chaque argument, si nécessaire.  Après la conversion, aucun paramètre n'est plus court que `int`, et aucun paramètre n'a le type **float** à moins que le type de paramètre soit explicitement spécifié comme **float** dans le prototype.  Cela signifie, par exemple, que la déclaration d'un paramètre comme `char` revient à la déclarer comme `int`.  
  
## Voir aussi  
 [Définitions de fonction C](../c-language/c-function-definitions.md)