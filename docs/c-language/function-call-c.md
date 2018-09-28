---
title: Appel de fonction (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48ddb3724e4c93135be57d1404ec51d5e885d4fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069818"
---
# <a name="function-call-c"></a>Appel de fonction (C)

Un *appel de fonction* est une expression qui inclut le nom de la fonction appelée ou la valeur d’un pointeur fonction et, éventuellement, les arguments passés à la fonction.

## <a name="syntax"></a>Syntaxe

*postfix-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**

*argument-expression-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *assignment-expression*

*postfix-expression* doit prendre la valeur d’une adresse de fonction (par exemple, un identificateur de fonction ou la valeur d’un pointeur fonction), et *argument-expression-list* est une liste d’expressions (séparées par des virgules) dont les valeurs (les arguments) sont passées à la fonction. L’argument *argument-expression-list* peut être vide.

Une expression de fonction d'appel a la valeur et le type de la valeur de retour de la fonction. Une fonction ne peut pas retourner d'objet de type tableau. Si le type de retour de la fonction est `void` (autrement dit si la fonction n'a jamais été déclarée pour retourner une valeur), l'expression d'appel de fonction a également le type `void`. (Pour plus d'informations, consultez [Appels de fonction](../c-language/function-calls.md).)

## <a name="see-also"></a>Voir aussi

[Opérateur d’appel de fonction](../cpp/function-call-operator-parens.md)