---
title: Littéraux chaîne dans les expressions primaires | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, in primary expressions
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5fd8c73bb9dac5a26c62b86bdc4038bd26a0829
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="string-literals-in-primary-expressions"></a>Littéraux chaîne dans les expressions primaires
Un littéral de chaîne est un caractère, un caractère élargi ou une séquence de caractères adjacents placés entre guillemets. Étant donné que les littéraux de chaîne et tous leurs éléments ne sont pas des variables, ils peuvent constituer l'opérande gauche d'une opération d'assignation. Le type d'un littéral de chaîne est un tableau de `char` (ou un tableau de `wchar_t` pour les littéraux de chaîne étendus). Les tableaux présents dans les expressions sont convertis en pointeurs. Pour plus d'informations sur les chaînes, consultez [Littéraux de chaîne](../c-language/c-string-literals.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions primaires C](../c-language/c-primary-expressions.md)