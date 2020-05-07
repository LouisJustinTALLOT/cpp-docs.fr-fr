---
title: Opérateurs suffixés
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: a86ede25feeaee3a9fb1c6b146cf9667b85c0c2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232245"
---
# <a name="postfix-operators"></a>Opérateurs suffixés

Les opérateurs suffixés ont la priorité la plus élevée (la liaison la plus étroite) dans l’évaluation de l’expression.

## <a name="syntax"></a>Syntaxe

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-List*<sub>OPT</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-***->***identificateur* d’expression    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*  **--**

Dans ce niveau de priorité, les opérateurs sont les indices de tableau, les appels de fonction, les membres de structure et d'union, et les opérateurs d'incrémentation et de décrémentation suffixés.

## <a name="see-also"></a>Voir aussi

[Opérateurs C](../c-language/c-operators.md)
