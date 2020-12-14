---
description: 'En savoir plus sur : opérateurs postfix'
title: Opérateurs suffixés
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: be8e7354d512174a4ab11ffcdcb82f9418baa894
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195864"
---
# <a name="postfix-operators"></a>Opérateurs suffixés

Les opérateurs suffixés ont la priorité la plus élevée (la liaison la plus étroite) dans l’évaluation de l’expression.

## <a name="syntax"></a>Syntaxe

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-List*<sub>OPT</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression* **->** *identificateur*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*  **--**

Dans ce niveau de priorité, les opérateurs sont les indices de tableau, les appels de fonction, les membres de structure et d'union, et les opérateurs d'incrémentation et de décrémentation suffixés.

## <a name="see-also"></a>Voir aussi

[Opérateurs C](../c-language/c-operators.md)
