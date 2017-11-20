---
title: "Opérateurs additifs C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5d41afccc7514c4e6469038b4f592890f9f355f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
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