---
description: 'En savoir plus sur : directives #ifdef et #ifndef (C/C++)'
title: '#ifdef et #ifndef, directives (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
ms.openlocfilehash: 4888e4516b57465974d99b1c9e8e6393e02f68c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269287"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>directives #ifdef et #ifndef (C/C++)

Les directives **#ifdef** et **#ifndef** ont le même effet que la directive [#if](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) lorsqu’elle est utilisée avec l’opérateur **défini** .

## <a name="syntax"></a>Syntaxe

>  *identificateur* de #ifdef\
>  *identificateur* de #ifndef

Ces directives sont équivalentes à ce qui suit :

> *identificateur* **défini par l' #if**\
> *identificateur* **#if ! défini**

## <a name="remarks"></a>Notes

Vous pouvez utiliser les directives **#ifdef** et **#ifndef** n’importe où `#if` peut être utilisé. L' **#ifdef** instruction d' *identificateur* est équivalente à `#if 1` lorsque *identifier* a été défini. Elle est équivalente à `#if 0` lorsque *identifier* n’a pas été défini ou a été non défini par la `#undef` directive. Ces directives vérifient uniquement la présence ou l'absence d'identificateurs définis avec `#define`, et non d'identificateurs déclarés dans le code source C ou C++.

Ces directives sont fournies uniquement pour des raisons de compatibilité avec les versions antérieures du langage. L’expression constante **définie (** *identificateur* **)** utilisée avec la `#if` directive est préférée.

La directive **#ifndef** vérifie l’inverse de la condition vérifiée par **#ifdef**. Si l’identificateur n’a pas été défini ou si sa définition a été supprimée avec `#undef` , la condition est vraie (différente de zéro). Sinon, la condition n'est pas vérifiée (0).

**Spécifique à Microsoft**

L' *identificateur* peut être passé à partir de la ligne de commande à l’aide de l’option [/d](../build/reference/d-preprocessor-definitions.md) . Jusqu’à 30 macros peuvent être spécifiées avec `/D` .

La directive **#ifdef** est utile pour vérifier si une définition existe, car une définition peut être passée à partir de la ligne de commande. Par exemple :

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
