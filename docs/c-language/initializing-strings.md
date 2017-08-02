---
title: "Initialisation de chaînes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c1bf614544f008910a86e8281cb775c1d7734b0d
ms.contentlocale: fr-fr
ms.lasthandoff: 05/18/2017

---
# <a name="initializing-strings"></a>Initialisation de chaînes
Vous pouvez initialiser un tableau de caractères (ou des caractères larges) avec un littéral de chaîne (ou un littéral de chaîne étendu). Exemple :  
  
```  
char code[ ] = "abc";  
```  
  
 initialise `code` en tant que tableau de caractères à quatre éléments. Le quatrième élément est le caractère Null, qui termine tous les littéraux de chaîne.  
  
 Une liste d'identificateurs ne peut pas dépasser le nombre d'identificateurs à initialiser. Si vous spécifiez une taille de tableau inférieure à celle de la chaîne, les caractères supplémentaires sont ignorés. Par exemple, la déclaration suivante initialise `code` en tant que tableau de caractères à trois éléments :  
  
```  
char code[3] = "abcd";  
```  
  
 Seuls les trois premiers caractères de l'initialiseur sont assignés à `code`. Le caractère `d` et le caractère Null de terminaison de la chaîne sont ignorés. Notez que cela crée une chaîne non terminée (autrement dit, une chaîne sans valeur 0 pour marquer sa terminaison) et génère un message de diagnostic indiquant cette condition.  
  
 La déclaration  
  
```  
char s[] = "abc", t[3] = "abc";  
```  
  
 est identique à  
  
```  
char s[]  = {'a', 'b', 'c', '\0'},   
     t[3] = {'a', 'b', 'c' };  
```  
  
 Si la chaîne est plus courte que la taille de tableau spécifiée, les éléments restants du tableau sont initialisés à 0.  
  
 **Section spécifique à Microsoft**  
  
 Dans Microsoft C, les littéraux de chaîne peuvent contenir jusqu'à 2048 octets au total.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Initialisation](../c-language/initialization.md)
