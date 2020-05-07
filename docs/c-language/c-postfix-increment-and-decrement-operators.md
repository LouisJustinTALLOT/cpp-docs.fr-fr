---
title: Opérateurs suffixés d'incrémentation et de décrémentation C
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
ms.openlocfilehash: 8c2e3ba50ce3e768b377a588cd3e82ad29df79ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325573"
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Opérateurs suffixés d'incrémentation et de décrémentation C

Les opérandes des opérateurs d’incrémentation et de décrémentation sont des types scalaires qui sont des valeurs lvalue modifiables.

## <a name="syntax"></a>Syntaxe

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*  **--**

Le résultat de l’opération d’incrémentation ou de décrémentation suffixée est la valeur de l’opérande. Une fois le résultat obtenu, la valeur de l'opérande est incrémentée (ou décrémentée). Le code suivant illustre l'opérateur d'incrémentation suffixée.

```
if( var++ > 0 )
    *p++ = *q++;
```

Dans cet exemple, la variable `var` est comparée à 0, puis incrémentée. Si `var` avait une valeur positive avant d'être incrémentée, l'instruction suivante est exécutée. D'abord, la valeur de l'objet pointé par `q`est assignée à l'objet pointé par `p`. Ensuite, `q` et `p` sont incrémentés.

## <a name="see-also"></a>Voir aussi

[Opérateurs suffixés d’incrémentation et de décrémentation : + + et--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)
