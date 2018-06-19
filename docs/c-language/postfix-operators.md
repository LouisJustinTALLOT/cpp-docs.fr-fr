---
title: Opérateurs suffixés | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14a23da2e8ed41954bd6faa2803d6e6c7dfb37a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384383"
---
# <a name="postfix-operators"></a>Opérateurs suffixés
Les opérateurs suffixés ont la priorité la plus élevée (la liaison la plus étroite) dans l’évaluation de l’expression.  
  
## <a name="syntax"></a>Syntaxe  
 *postfix-expression* :  
 *primary-expression*  
  
 *postfix-expression*  **[**  *expression*  **]**  
  
 *postfix-expression*  **(**  *argument-expression-list* opt **)**  
  
 *postfix-expression*  **.**  *identifier*  
  
 *postfix-expression*  **->**  *identifier*  
  
 *postfix-expression*  **++**  
  
 *postfix-expression*  **--**  
  
 Dans ce niveau de priorité, les opérateurs sont les indices de tableau, les appels de fonction, les membres de structure et d'union, et les opérateurs d'incrémentation et de décrémentation suffixés.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs C](../c-language/c-operators.md)