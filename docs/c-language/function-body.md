---
title: Corps de fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6a566c1120f0a89a985895393fae5a79690bfa3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="function-body"></a>Corps de fonction
Un « corps de fonction » est une instruction composée contenant les instructions qui spécifient ce que fait la fonction.  
  
## <a name="syntax"></a>Syntaxe  
 *function-definition*:  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* est spécifique de Microsoft */  
  
 *compound-statement*: /\* Le corps de la fonction \*/  
 **{**  *declaration-list* opt*statement-list* opt **}**  
  
 Les variables déclarées dans un corps de fonction, appelées « variables locales », ont une classe de stockage **auto** sauf indication contraire. Lorsque la fonction est appelée, du stockage est créé pour les variables locales et les initialisations locales sont exécutées. Le contrôle d'exécution passe à la première instruction dans *compound-statement* et continue jusqu'à ce qu'une instruction `return` soit exécutée ou jusqu'à la fin du corps de la fonction. Le contrôle revient ensuite au point auquel la fonction a été appelée.  
  
 Une instruction `return` contenant une expression doit être exécutée si la fonction doit retourner une valeur. La valeur de retour d'une fonction est non définie si aucune instruction `return` n'est exécutée ou si l'instruction `return` n'inclut pas d'expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Définitions de fonction C](../c-language/c-function-definitions.md)