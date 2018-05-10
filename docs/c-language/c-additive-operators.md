---
title: Opérateurs additifs C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df491508f7898fe3c97bc02a83e5259baa9c89f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="c-additive-operators"></a>Opérateurs additifs C
Les opérateurs additifs exécutent une addition (**+**) et une soustraction (**-**).  
  
## <a name="syntax"></a>Syntaxe  
 *additive-expression* :  
 *multiplicative-expression*  
  
 *additive-expression*  **+**  *multiplicative-expression*  
  
 *additive-expression*  **-**  *multiplicative-expression*  
  
> [!NOTE]
>  Même si la syntaxe de l’élément *additive-expression* comprend *multiplicative-expression*, cela n’implique pas l’obligation d’utiliser des expressions avec multiplication. Consultez la syntaxe dans [Résumé de syntaxe du langage C](../c-language/c-language-syntax-summary.md), pour les éléments *multiplicative-expression*, *cast-expression* et *unary-expression*.  
  
 Les opérandes peuvent être des valeurs intégrales ou flottantes. Certaines opérations additives peuvent également être exécutées sur des valeurs de pointeur, comme l'indique la description de chaque opérateur.  
  
 Les opérateurs additifs exécutent les conversions arithmétiques habituelles sur les opérandes de type entier et flottant. Le type du résultat est le type des opérandes après conversion. Étant donné que les conversions exécutées par les opérateurs additifs ne fournissent pas de conditions de dépassement de capacité positif ou de dépassement de capacité négatif, les informations risquent d’être perdues si le résultat d’une opération additive ne peut pas être représenté dans le type des opérandes après conversion.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs additifs : + et -](../cpp/additive-operators-plus-and.md)