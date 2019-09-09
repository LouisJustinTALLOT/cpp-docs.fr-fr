---
title: inline_recursion, pragma
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 0169e06e8e47f7b0a7b3f73e809ddc988bcf1e95
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220955"
---
# <a name="inline_recursion-pragma"></a>inline_recursion, pragma

Contrôle l'expansion inline des appels de fonction directe ou mutuellement récursive.

## <a name="syntax"></a>Syntaxe

> **#pragma inline_recursion (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Notes

Utilisez ce pragma pour contrôler les fonctions marquées comme [inline](../cpp/inline-functions-cpp.md) [et _ _ inline ou](../cpp/inline-functions-cpp.md) les fonctions que le `/Ob2` compilateur développe automatiquement sous l’option. L’utilisation de ce pragma requiert une option du compilateur [/ob](../build/reference/ob-inline-function-expansion.md) définie sur 1 ou 2. L’État par défaut pour **inline_recursion** est OFF. Ce pragma prend effet au premier appel de fonction après que le pragma a été affiché et n’affecte pas la définition de la fonction.

Le pragma **inline_recursion** contrôle le développement des fonctions récursives. Si **inline_recursion** est désactivé et si une fonction Inline s’appelle elle-même, directement ou indirectement, la fonction est développée une seule fois. Si **inline_recursion** est activé, la fonction est développée plusieurs fois jusqu’à ce qu’elle atteigne la valeur définie avec le pragma [inline_depth](../preprocessor/inline-depth.md) , la valeur par défaut pour les fonctions récursives qui est définie par le `inline_depth` pragma, ou une limite de capacité.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob (Expansion des fonctions Inline)](../build/reference/ob-inline-function-expansion.md)
