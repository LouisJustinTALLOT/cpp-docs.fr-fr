---
title: /Zc (Conformité)
description: Les options du compilateur de conformité/ZC activent ou désactivent la prise en charge de la conformité ou du comportement à compatibilité descendante.
ms.date: 09/10/2020
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 13e06cd75f1ee684c2ee1ad6239aeb77b805675e
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041521"
---
# <a name="zc-conformance"></a>`/Zc` Conformité

Vous pouvez utiliser les **`/Zc`** Options du compilateur pour spécifier le comportement du compilateur standard ou spécifique à Microsoft.

## <a name="syntax"></a>Syntaxe

> **`/Zc:`**_option_{,_option_}

## <a name="remarks"></a>Remarques

Lorsque Visual Studio a implémenté une extension en C ou C++ qui n’est pas compatible avec la norme, vous pouvez utiliser une **`/Zc`** option de conformité pour spécifier un comportement conforme ou spécifique à Microsoft. Pour certaines options, le comportement spécifique à Microsoft est la valeur par défaut, pour empêcher les modifications importantes à grande échelle du code existant. Dans d’autres cas, la valeur par défaut est le comportement standard, où les améliorations de la sécurité, des performances ou de la compatibilité l’emportent sur les coûts des modifications avec rupture. Le paramètre par défaut de chaque option de conformité peut changer dans les versions plus récentes de Visual Studio. Pour plus d’informations sur chaque option de conformité, consultez la rubrique relative à l’option spécifique. L' [`/permissive-`](permissive-standards-conformance.md) option de compilateur définit implicitement les options de conformité qui ne sont pas définies par défaut sur leur paramètre conforme.

Voici les **`/Zc`** Options du compilateur :

| Option | Comportement |
|--|--|
| [`/Zc:alignedNew`](zc-alignednew.md) | Activez l’allocation dynamique sur-alignée C++ 17 (activé par défaut dans C++ 17). |
| [`/Zc:auto`](zc-auto-deduce-variable-type.md) | Appliquer la nouvelle signification C++ standard pour **`auto`** (activé par défaut). |
| [`/Zc__cplusplus`](zc-cplusplus.md) | Activez la `__cplusplus` macro pour signaler le standard pris en charge (désactivé par défaut). |
| [`/Zc:externConstexpr`](zc-externconstexpr.md) | Activez la liaison externe pour les **`constexpr`** variables (désactivé par défaut). |
| [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) | Appliquer les **`for`** règles de portée C++ standard (activé par défaut). |
| [`/ZcimplicitNoexcept`](zc-implicitnoexcept-implicit-exception-specifiers.md) | Activez implicite **`noexcept`** sur les fonctions requises (activé par défaut). |
| [`/Zc:inline`](zc-inline-remove-unreferenced-comdat.md) | Supprimez la fonction ou les données non référencées si elle est COMDAT ou si elle a uniquement une liaison interne (désactivée par défaut). |
| [`/Zc:noexceptTypes`](zc-noexcepttypes.md) | Appliquer les règles C++ 17 **`noexcept`** (activé par défaut dans c++ 17 ou version ultérieure). |
| [`/Zc:preprocessor`](zc-preprocessor.md) | Utilisez le nouveau préprocesseur conforme (désactivé par défaut, sauf dans C11/C17). |
| [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) | Un type temporaire UDT ne sera pas lié à une référence lvalue non const (désactivé par défaut). |
| [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) | Appliquer les règles de conversion de type explicite C++ standard (désactivées par défaut). |
| [`/Zc:sizedDealloc`](zc-sizeddealloc-enable-global-sized-dealloc-functions.md) | Activez les fonctions de désallocation dimensionnées globales de C++ 14 (activé par défaut). |
| [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) | Désactive la conversion de littéral de chaîne en `char*` ou `wchar_t*` (désactivé par défaut). |
| [`/Zc:ternary`](zc-ternary.md) | Applique les règles d’opérateur conditionnel sur les types d’opérandes (désactivés par défaut). |
| [`/Zc:threadSafeInit`](zc-threadsafeinit-thread-safe-local-static-initialization.md) | Activez l’initialisation statique locale thread-safe (activée par défaut). |
| [`/Zc:throwingNew`](zc-throwingnew-assume-operator-new-throws.md) | Supposer que **`operator new`** lève une exception en cas d’échec (désactivé par défaut). |
| [`/Zc:trigraphs`](zc-trigraphs-trigraphs-substitution.md) | Activer les trigraphes (obsolète, désactivé par défaut). |
| [`/Zc:twoPhase`](zc-twophase.md) | Utilisez le comportement d’analyse de modèle non conforme (conforme par défaut). |
| [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) | **`wchar_t`** est un type natif, et non un typedef (activé par défaut). |

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
