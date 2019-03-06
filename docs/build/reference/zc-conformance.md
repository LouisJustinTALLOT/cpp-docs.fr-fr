---
title: /Zc (Conformité)
ms.date: 03/06/2018
f1_keywords:
- /zc
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 50f3e7a79b80514b6c28bd9aee86c720d6e20cf6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413912"
---
# <a name="zc-conformance"></a>/Zc (Conformité)

Vous pouvez utiliser la **/Zc** options du compilateur pour spécifier le comportement de compilateur standard ou spécifique à Microsoft.

## <a name="syntax"></a>Syntaxe

> **/Zc:**_option_{,_option_}

## <a name="remarks"></a>Notes

Lorsque Visual Studio a implémenté une extension de C ou C++ qui n’est pas compatible avec la norme, vous pouvez utiliser un `/Zc` option de conformité pour spécifier le comportement conforme à la norme ou spécifiques à Microsoft. Pour certaines options, le comportement spécifique de Microsoft est la valeur par défaut, pour empêcher des modifications avec rupture à grande échelle au code existant. Dans d’autres cas, la valeur par défaut est le comportement standard, où les améliorations de sécurité, performances ou la compatibilité l’emportent sur les coûts de modifications avec rupture. Le paramètre par défaut de chaque option de la conformité peut changer dans les versions plus récentes de Visual Studio. Pour plus d’informations sur chaque option de conformité, consultez la rubrique de l’option spécifique. Le [/ permissive-](permissive-standards-conformance.md) option du compilateur définit implicitement les options de mise en conformité qui ne sont pas définies par défaut pour leur paramètre conforme.

Il s’agit de la `/Zc` options du compilateur :

|Option|Comportement|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Activer C ++ 17 suralignés allocation dynamique (activé par défaut dans C ++ 17).|
|[auto\[-\]](zc-auto-deduce-variable-type.md)|Appliquer la nouvelle signification C++ Standard pour `auto` (sur par défaut).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Activer la **__cplusplus** macro pour signaler le standard pris en charge (désactivé par défaut).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Activer une liaison externe pour `constexpr` variables (désactivé par défaut).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Appliquer la norme C++ `for` règles de portée (sur par défaut).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Activer implicite `noexcept` sur les fonctions obligatoires (sur par défaut).|
|[inline\[-\]](zc-inline-remove-unreferenced-comdat.md)|Supprimer une fonction non référencée ou des données si elle est COMDAT ou a une liaison interne uniquement (désactivé par défaut).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Appliquer les règles de noexcept C ++ 17 (sur par défaut dans C ++ 17 ou version ultérieure).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Une table temporaire UDT n’est pas liée à une référence non const lvalue (désactivé par défaut).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Appliquer les règles de conversion de type explicite Standard C++ (désactivé par défaut).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Activer les fonctions de global désallocation dimensionnée C ++ 14 (sur par défaut).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Désactiver le littéral de chaîne en `char*` ou `wchar_t*` conversion (désactivé par défaut).|
|[ternary\[-\]](zc-ternary.md)|Appliquer les règles de l’opérateur conditionnel sur les types d’opérande (désactivé par défaut).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Activer l’initialisation statique locale thread-safe (sur par défaut).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Supposons que `operator new` lève en cas d’échec (désactivé par défaut).|
|[trigraphs\[-\]](zc-trigraphs-trigraphs-substitution.md)|Activer les trigraphes (obsolètes, désactivé par défaut).|
|[twoPhase-](zc-twophase.md)|Utilisez l’analyse du comportement (conforme par défaut) de modèle non conforme.|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` est un type natif, et non un typedef (sur par défaut).|

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Voir aussi

[Options du compilateur](compiler-options.md)<br/>
[Définition des options du compilateur](setting-compiler-options.md)
