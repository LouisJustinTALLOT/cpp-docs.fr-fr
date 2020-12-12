---
description: 'En savoir plus sur:/Zc : throwingNew (supposer les nouvelles levées de l’opérateur)'
title: /Zc:throwingNew (Supposer de nouvelles levées d’exception de l’opérateur)
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
ms.openlocfilehash: 83a78c62328853bdaf9515b55bef72503d166b58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271198"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (Supposer de nouvelles levées d’exception de l’opérateur)

Lorsque l’option **/Zc : throwingNew** est spécifiée, le compilateur optimise les appels à `operator new` pour ignorer les vérifications d’un retour de pointeur null. Cette option indique au compilateur de supposer que toutes les implémentations liées d’et d' `operator new` allocateurs personnalisés sont conformes à la norme C++ et lèvent en cas d’échec d’allocation. Par défaut dans Visual Studio, le compilateur pessimistically génère des contrôles de valeur null (**/Zc : throwingNew-**) pour ces appels, car les utilisateurs peuvent établir une liaison avec une implémentation sans levée de `operator new` ou écrire des routines d’allocation personnalisées qui retournent des pointeurs null.

## <a name="syntax"></a>Syntaxe

> **/Zc : throwingNew**[ **-** ]

## <a name="remarks"></a>Notes

Depuis la norme ISO C++ 98, la norme a spécifié que l’opérateur par défaut New lève une exception en cas d’échec [de](../../standard-library/new-operators.md#op_new) l’allocation de `std::bad_alloc` mémoire. Les versions de Visual C++ jusqu’à Visual Studio 6,0 retournaient un pointeur null sur un échec d’allocation. À compter de Visual Studio 2002, est `operator new` conforme à la norme et lève une exception en cas d’échec. Pour prendre en charge le code qui utilise l’ancien style d’allocation, Visual Studio fournit une implémentation pouvant être liée de `operator new` dans nothrownew. obj qui retourne un pointeur null en cas d’échec. Par défaut, le compilateur génère également des vérifications de valeur null défensives pour empêcher ces allocateurs de style plus anciens de provoquer un incident immédiat en cas d’échec. L’option **/Zc : throwingNew** indique au compilateur de conserver ces contrôles de valeur null, en partant du principe que tous les allocateurs de mémoire liés sont conformes à la norme. Cela ne s’applique pas aux surcharges explicites sans levée `operator new` , qui sont déclarées à l’aide d’un paramètre supplémentaire de type `std::nothrow_t` et qui ont une **`noexcept`** spécification explicite.

Conceptuellement, pour créer un objet sur le magasin gratuit, le compilateur génère du code pour allouer sa mémoire, puis appeler son constructeur pour initialiser la mémoire. Étant donné que le compilateur MSVC ne peut normalement pas déterminer si ce code sera lié à un allocateur non conforme et non levant, par défaut, il génère également une vérification de valeur null avant d’appeler le constructeur. Cela empêche la déréférencement d’un pointeur null dans l’appel de constructeur si une allocation sans levée échoue. Dans la plupart des cas, ces contrôles ne sont pas nécessaires, car les `operator new` allocateurs par défaut lèvent au lieu de retourner des pointeurs null. Les contrôles ont également des effets secondaires indésirables. Ils encombrent la taille du code, ils inondent le prédiction de branche et empêchent d’autres optimisations de compilateur utiles, telles que la dévirtualisation ou la propagation const de l’objet initialisé. Les contrôles existent uniquement pour prendre en charge le code lié à *nothrownew. obj* ou ayant des implémentations personnalisées non conformes `operator new` . Si vous n’utilisez pas de non-conformité `operator new` , nous vous recommandons d’utiliser **/Zc : throwingNew** pour optimiser votre code.

L’option **/Zc : throwingNew** est désactivée par défaut et n’est pas affectée par l’option [/permissive-](permissive-standards-conformance.md) .

Si vous compilez à l’aide de la génération de code durant l’édition de liens (LTCG), vous n’avez pas besoin de spécifier **/Zc : throwingNew**. Lorsque votre code est compilé à l’aide de LTCG, le compilateur peut détecter si l’implémentation conforme par défaut `operator new` est utilisée. Si c’est le cas, le compilateur quitte automatiquement les contrôles de valeur null. L’éditeur de liens recherche l’indicateur **/ThrowingNew** pour déterminer si l’implémentation de `operator new` est conforme. Vous pouvez spécifier cet indicateur à l’éditeur de liens en incluant cette directive dans la source pour votre nouvelle implémentation d’opérateur personnalisé :

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le menu déroulant **configuration** , choisissez **toutes les configurations**.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **options supplémentaires** pour inclure **/Zc : throwingNew** ou **/Zc : ThrowingNew-** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Spécifications d’exception (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Terminate (exception)](../../standard-library/exception-functions.md#terminate)<br/>
