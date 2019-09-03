---
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
ms.openlocfilehash: 433076388f3646b19d75a907c6b2254098096688
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220104"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>directives #ifdef et #ifndef (C/C++)

Les directives **#ifdef** et **#ifndef** ont le même effet que la directive [#if](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) lorsqu’elle est utilisée avec l’opérateur **défini** .

## <a name="syntax"></a>Syntaxe

> **#ifdef** *identificateur*\
> **#ifndef** *identificateur*

Ces directives sont équivalentes à ce qui suit:

> **#if défini** *identificateur*\
> **#if! défini** *identificateur*

## <a name="remarks"></a>Notes

Vous pouvez utiliser les directives **#ifdef** et **#ifndef** n' `#if` importe où peut être utilisé. L' **#ifdef** instruction d' *identificateur* est équivalente `#if 1` à lorsque *identifier* a été défini. Elle est équivalente `#if 0` à lorsque *identifier* n’a pas été défini ou a été non défini par la `#undef` directive. Ces directives vérifient uniquement la présence ou l'absence d'identificateurs définis avec `#define`, et non d'identificateurs déclarés dans le code source C ou C++.

Ces directives sont fournies uniquement pour des raisons de compatibilité avec les versions antérieures du langage. L’expression constante **définie (** *identificateur* **)** utilisée avec la `#if` directive est préférée.

La directive **#ifndef** vérifie l’inverse de la condition vérifiée par **#ifdef**. Si l’identificateur n’a pas été défini ou si sa définition a été supprimée avec `#undef`, la condition est vraie (différente de zéro). Sinon, la condition n'est pas vérifiée (0).

**Section spécifique à Microsoft**

L' *identificateur* peut être passé à partir de la ligne de commande à l’aide de l’option [/d](../build/reference/d-preprocessor-definitions.md) . Jusqu’à 30 macros peuvent être spécifiées `/D`avec.

La directive **#ifdef** est utile pour vérifier si une définition existe, car une définition peut être passée à partir de la ligne de commande. Par exemple :

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
