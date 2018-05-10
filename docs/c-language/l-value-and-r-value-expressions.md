---
title: Expressions L-Value et R-Value | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 654805750b3cd17e2157fa3710791493970b371f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="l-value-and-r-value-expressions"></a>Expressions L-Value et R-Value
Les expressions qui font référence à des emplacements de mémoire sont appelées expressions « l-value ». Une l-value représente la valeur « localisateur » d’une zone de stockage, ou une valeur « gauche », ce qui implique qu’elle peut apparaître à gauche du signe égal à (**=**). Les l-values sont souvent des identificateurs.  
  
 Les expressions faisant référence à des emplacements modifiables sont appelées « l-values modifiables ». Une l-value modifiable ne peut pas être définie avec un type de tableau, un type incomplet ou un type avec l’attribut **const**. Pour que les structures et les unions soient des l-values modifiables, elles ne doivent comporter aucun membre défini avec l’attribut **const**. Le nom de l'identificateur désigne un emplacement de stockage, alors que la valeur de la variable est la valeur stockée à cet emplacement.  
  
 Un identificateur est une l-value modifiable si elle fait référence à un emplacement mémoire et si son type est arithmétique, structure, union ou pointeur. Par exemple, si `ptr` est un pointeur vers une zone de stockage, `*ptr` est une l-value modifiable qui désigne la zone de stockage vers laquelle `ptr` pointe.  
  
 Les expressions C suivantes peuvent être des expressions l-value :  
  
-   Un identificateur de type intégral, flottant, pointeur, structure ou union  
  
-   Une expression d’indice (**[ ]**) qui ne correspond pas à un tableau  
  
-   Une expression de sélection de membres (**->** ou **.**)  
  
-   Une expression indirection-unaire (**\***) qui ne fait pas référence à un tableau  
  
-   Une expression l-value entre parenthèses  
  
-   Un objet **const** (une l-value non modifiable)  
  
 Le terme « r- value » est parfois utilisé pour décrire la valeur d'une expression et pour établir une distinction par rapport à une l-value. Toutes les l-values sont des r- values, mais les r- values ne sont pas toutes des l-values.  
  
 **Section spécifique à Microsoft**  
  
 Microsoft C inclut une extension vers la norme C ANSI qui permet d’effectuer un cast sur des l-values à utiliser en tant que l-values, à condition que la taille de l’objet ne soit pas rallongée lors de cette opération. Pour plus d’informations, consultez [Conversions de cast de type](../c-language/type-cast-conversions.md). L’exemple suivant illustre cette fonctionnalité :  
  
```  
char *p ;  
short  i;  
long l;  
  
(long *) p = &l ;       /* Legal cast   */  
(long) i = l ;          /* Illegal cast */  
```  
  
 Par défaut pour Microsoft C, les extensions Microsoft sont activées. Utilisez l’option du compilateur /Za pour désactiver ces extensions.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Opérandes et expressions](../c-language/operands-and-expressions.md)