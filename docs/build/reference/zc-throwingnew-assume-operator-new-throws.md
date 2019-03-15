---
title: /Zc:throwingNew (supposer opérateur de nouvelles levées)
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: c8c7b4e7246cc3bb1b3a73cde4f6830eb7178dd2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813511"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (supposer opérateur de nouvelles levées)

Lorsque le **/Zc:throwingNew** est spécifiée, le compilateur optimise les appels à `operator new` d’ignorer les contrôles d’un pointeur null en retour. Cette option indique au compilateur de supposer que tous les liés des implémentations de `operator new` et allocateurs personnalisés sont conformes à la norme C++ et lever en cas d’échec d’allocation. Par défaut dans Visual Studio, le compilateur génère pessimiste vérifications « null » (**/Zc:throwingNew-**) pour ces appels, étant donné que les utilisateurs peuvent lier avec une implémentation non lanceurs de `operator new` ou écrire des routines de l’allocateur personnalisé qui retournent des pointeurs null.

## <a name="syntax"></a>Syntaxe

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>Notes

La norme ISO C ++ 98, depuis l’a spécifié que la valeur par défaut [opérateur new](../../standard-library/new-operators.md#op_new) lève `std::bad_alloc` lorsque l’allocation de mémoire échoue. Versions de Visual C++ dans Visual Studio 6.0 a retourné un pointeur null sur un échec d’allocation. À compter de Visual Studio 2002, `operator new` conforme au standard et lève en cas d’échec. Pour prendre en charge de code qui utilise l’ancien style d’allocation, Visual Studio fournit une implémentation pouvant être liée de `operator new` dans nothrownew.obj qui retourne un pointeur null en cas d’échec. Par défaut, le compilateur génère également des contrôles de valeur null défensives pour empêcher ces allocateurs anciens provoque un blocage immédiat en cas d’échec. Le **/Zc:throwingNew** option indique au compilateur d’omettre ces vérifications « null », sur l’hypothèse que tous les liés mémoire allocateurs sont conformes à la norme. Cela ne s’applique pas à non lever explicite `operator new` surcharges, qui sont déclarés à l’aide d’un paramètre supplémentaire de type `std::nothrow_t` et avez explicite `noexcept` spécification.

Conceptuellement, pour créer un objet dans le magasin libre, le compilateur génère du code pour allouer la mémoire, puis à appeler son constructeur pour initialiser la mémoire. Étant donné que le compilateur MSVC normalement ne peut pas déterminer si ce code sera lié à un allocateur non conformes, pas d’exceptions, par défaut il génère également une vérification de valeur null avant d’appeler le constructeur. Cela empêche un pointeur null dans l’appel de constructeur de déréférencement si une allocation non lanceurs échoue. Dans la plupart des cas, ces vérifications sont inutiles, étant donné que la valeur par défaut `operator new` allocateurs lever au lieu de retourner des pointeurs null. Les vérifications ont également fâcheux effets secondaires. Ils enfler la taille du code, ils inondent PRÉDICTEUR de branche, et ils empêchent les autres optimisations du compilateur utiles telles que devirtualization ou const propagation hors de l’objet initialisé. Les vérifications existent uniquement au code de prise en charge des liens vers *nothrownew.obj* ou a non conformes personnalisé `operator new` implémentations. Si vous n’utilisez pas non conformes `operator new`, nous vous recommandons d’utiliser **/Zc:throwingNew** d’optimiser votre code.

Le **/Zc:throwingNew** option est désactivée par défaut et n’est pas affectée par le [/ permissive-](permissive-standards-conformance.md) option.

Si vous compilez à l’aide de la génération de code de l’édition de liens (LTCG), vous n’avez pas besoin de spécifier **/Zc:throwingNew**. Lorsque votre code est compilé à l’aide de LTCG, le compilateur peut détecter si la valeur par défaut, conforme `operator new` implémentation est utilisée. Dans ce cas, le compilateur omet automatiquement les contrôles de valeur null. L’éditeur de liens recherche le **/ThrowingNew** indicateur pour indiquer si l’implémentation de `operator new` est conforme. Vous pouvez spécifier cet indicateur pour l’éditeur de liens en incluant cette directive dans la source pour votre implémentation de nouvel opérateur personnalisé :

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. À partir de la **Configuration** menu déroulant, choisissez **toutes les Configurations**.

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc:throwingNew** ou **/Zc:throwingNew-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Spécifications d’exception (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[terminate (exception)](../../standard-library/exception-functions.md#terminate)<br/>
