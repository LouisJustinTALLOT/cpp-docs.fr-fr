---
title: '#Directives ifdef et #ifndef (C/C++)'
ms.date: 11/04/2016
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
ms.openlocfilehash: d7a6a1604df03f0607f33e42880270cbdcd62e8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409874"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>Directives #ifdef et #ifndef (C/C++)
Le **#ifdef** et **#ifndef** directives effectuant la même tâche que le `#if` directive lorsqu’il est utilisé avec **défini**( *identificateur* ).

## <a name="syntax"></a>Syntaxe

```
#ifdef identifier
#ifndef identifier

// equivalent to
#if defined identifier
#if !defined identifier
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser la **#ifdef** et **#ifndef** directives n’importe où `#if` peut être utilisé. Le **#ifdef** *identificateur* instruction est équivalente à `#if 1` lorsque *identificateur* a été défini, et il est équivalent à `#if 0` lorsque *identificateur* n’a pas été défini ou a été supprimée avec la `#undef` directive. Ces directives vérifient uniquement la présence ou l'absence d'identificateurs définis avec `#define`, et non d'identificateurs déclarés dans le code source C ou C++.

Ces directives sont fournies uniquement pour des raisons de compatibilité avec les versions antérieures du langage. Le **défini (** *identificateur* **)** expression constante utilisée avec la `#if` directive est préférée.

Le **#ifndef** directive vérifie l’inverse de la condition vérifiée par **#ifdef**. Si l'identificateur n'a pas été défini (ou si sa définition a été supprimée avec `#undef`), la condition est vraie (non nulle). Sinon, la condition n'est pas vérifiée (0).

**Section spécifique à Microsoft**

Le *identificateur* peuvent être passés à partir de la ligne de commande à l’aide de la `/D` option. Jusqu'à 30 macros peut être spécifiée avec `/D`.

Cela est utile pour vérifier si une définition existe, car une définition peut être transmise à partir de la ligne de commande. Exemple :

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