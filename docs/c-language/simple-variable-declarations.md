---
title: "Déclarations de variables simples | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dd5ab69e0e6621324f04008c34b2a52dcbd20787
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="simple-variable-declarations"></a>Déclarations de variables simples
La déclaration d'une variable simple, la forme la plus simple d'un déclarateur direct, spécifie le nom et le type de la variable. Elle spécifie également la classe de stockage et le type de données de la variable.  
  
 Les classes de stockage ou les types (ou les deux) sont requis sur les déclarations de variables. Les variables non typées (telles que `var;`) génèrent des avertissements.  
  
## <a name="syntax"></a>Syntaxe  
 `declarator`:  
 *pointer* opt  
  
 *direct-declarator*  
  
 *direct-declarator* :  
 *identifier*  
  
 *identificateur* :  
 *nondigit*  
  
 *identifier nondigit*  
  
 *identifier digit*  
  
 Pour les types arithmétiques, de structure, d'union, d'énumération et void, ainsi que pour les types représentés par des noms `typedef`, des déclarateurs simples peuvent être utilisés dans une déclaration car le spécificateur de type fournit toutes les informations de saisie. Les types de pointeur, de tableau et de fonction nécessitent des déclarateurs plus complexes.  
  
 Vous pouvez utiliser une liste d'identificateurs séparés par une virgule (**,**) pour spécifier plusieurs variables dans la même déclaration. Toutes les variables définies dans la déclaration ont le même type de base. Exemple :  
  
```  
int x, y;        /* Declares two simple variables of type int */  
int const z = 1; /* Declares a constant value of type int */  
```  
  
 Les variables `x` et `y` peuvent contenir n'importe quelle valeur de l'ensemble définie par le type `int` pour une implémentation particulière. L'objet simple `z` est initialisé à 1 et n'est pas modifiable.  
  
 Si la déclaration de `z` concernait une variable statique non initialisée ou était dans la portée du fichier, elle recevrait la valeur initiale 0, et cette valeur ne serait pas modifiable.  
  
```  
unsigned long reply, flag; /* Declares two variables  
                              named reply and flag     */  
```  
  
 Dans cet exemple, les deux variables `reply` et `flag` ont le type `unsigned long` et contiennent des valeurs intégrales non signées.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)