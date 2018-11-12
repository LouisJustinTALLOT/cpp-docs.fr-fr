---
title: Opérateurs suffixés
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: 45f7b67b62657c498bdd9ebcf5d85379cdcdd211
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440702"
---
# <a name="postfix-operators"></a>Opérateurs suffixés

Les opérateurs suffixés ont la priorité la plus élevée (la liaison la plus étroite) dans l’évaluation de l’expression.

## <a name="syntax"></a>Syntaxe

*postfix-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **->**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

Dans ce niveau de priorité, les opérateurs sont les indices de tableau, les appels de fonction, les membres de structure et d'union, et les opérateurs d'incrémentation et de décrémentation suffixés.

## <a name="see-also"></a>Voir aussi

[Opérateurs C](../c-language/c-operators.md)