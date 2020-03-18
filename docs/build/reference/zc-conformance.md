---
title: /Zc (Conformité)
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 4422524deab2a749c96d5e967bc3223d0c9c9873
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438673"
---
# <a name="zc-conformance"></a>/Zc (Conformité)

Vous pouvez utiliser les options du compilateur **/Zc** pour spécifier le comportement de compilateur standard ou spécifique à Microsoft.

## <a name="syntax"></a>Syntaxe

> **/Zc :** _option_{,_option_}

## <a name="remarks"></a>Notes

Lorsque Visual Studio a implémenté une extension dans C ou C++ qu’il n’est pas compatible avec la norme, vous pouvez utiliser une option de conformité `/Zc` pour spécifier un comportement conforme ou spécifique à Microsoft. Pour certaines options, le comportement spécifique à Microsoft est la valeur par défaut, pour empêcher les modifications importantes à grande échelle du code existant. Dans d’autres cas, la valeur par défaut est le comportement standard, où les améliorations de la sécurité, des performances ou de la compatibilité l’emportent sur les coûts des modifications avec rupture. Le paramètre par défaut de chaque option de conformité peut changer dans les versions plus récentes de Visual Studio. Pour plus d’informations sur chaque option de conformité, consultez la rubrique relative à l’option spécifique. L’option de compilateur [/permissive-](permissive-standards-conformance.md) définit implicitement les options de conformité qui ne sont pas définies par défaut sur leur paramètre conforme.

Voici les options du compilateur `/Zc` :

|Option|Comportement|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Activez l’allocation dynamique sur-alignée C++ 17 (activé par défaut dans C++ 17).|
|[\[automatique -\]](zc-auto-deduce-variable-type.md)|Appliquer la nouvelle signification C++ Standard pour `auto` (activé par défaut).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Activez la macro **__cplusplus** pour signaler le standard pris en charge (désactivé par défaut).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Activez la liaison externe pour les variables de `constexpr` (désactivé par défaut).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Appliquer les C++ règles de portée de `for` standard (activé par défaut).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Activez les `noexcept` implicites sur les fonctions requises (activé par défaut).|
|[-de\[Inline \]](zc-inline-remove-unreferenced-comdat.md)|Supprimez la fonction ou les données non référencées si elle est COMDAT ou si elle a uniquement une liaison interne (désactivée par défaut).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Appliquer les règles noexcept C++ 17 (activé par défaut dans C++ 17 ou version ultérieure).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Un type temporaire UDT ne sera pas lié à une référence lvalue non const (désactivé par défaut).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Appliquer les C++ règles de conversion de type explicite standard (désactivé par défaut).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Activez les fonctions de désallocation dimensionnées globales de C++ 14 (activé par défaut).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Désactiver le littéral de chaîne pour `char*` ou `wchar_t*` la conversion (désactivé par défaut).|
|[\] de -\[ternaire](zc-ternary.md)|Applique les règles d’opérateur conditionnel sur les types d’opérandes (désactivés par défaut).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Activez l’initialisation statique locale thread-safe (activée par défaut).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Supposons que `operator new` lève une exception en cas d’échec (désactivé par défaut).|
|[trigraphes\[-\]](zc-trigraphs-trigraphs-substitution.md)|Activer les trigraphes (obsolète, désactivé par défaut).|
|[twoPhase](zc-twophase.md)|Utilisez le comportement d’analyse de modèle non conforme (conforme par défaut).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` est un type natif, et non un typedef (activé par défaut).|

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
