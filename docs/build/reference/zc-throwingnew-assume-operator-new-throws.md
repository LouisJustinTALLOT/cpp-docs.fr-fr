---
title: /Zc:throwingNew (lève nouvel opérateur supposé) | Documents Microsoft
ms.custom: ''
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- throwingNew
- /Zc:throwingNew
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f446e5c71e88be86c31e5a83ca7d23f611683af4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383460"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (supposer que lève nouvel opérateur)

Lorsque le **/Zc:throwingNew** est spécifiée, le compilateur optimise les appels à `operator new` pour ignorer les contrôles d’un pointeur null en retour. Cette option indique au compilateur de supposer que tous les liés implémentations de `operator new` et allocateurs personnalisés conforme à la norme C++ et lever en cas d’échec d’allocation. Par défaut dans Visual Studio, le compilateur génère pessimiste les vérifications null (**/Zc:throwingNew-**) pour ces appels, car les utilisateurs peuvent lier avec une implémentation non lanceurs de `operator new` ou écrire des routines de l’allocateur personnalisé qui retournent des pointeurs null.

## <a name="syntax"></a>Syntaxe

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>Notes

La norme ISO C ++ 98, depuis l’a spécifié que la valeur par défaut [new, opérateur](../../standard-library/new-operators.md#op_new) lève `std::bad_alloc` lorsque l’allocation de mémoire échoue. Versions de Visual C++ jusqu'à Visual Studio 6.0 a retourné un pointeur null en cas d’un échec d’allocation. À compter de Visual Studio 2002, `operator new` conforme au standard et lève en cas d’échec. Pour prendre en charge le code qui utilise l’ancien style d’allocation, Visual Studio fournit une implémentation de fenêtres de `operator new` dans nothrownew.obj qui retourne un pointeur null en cas d’échec. Par défaut, le compilateur génère également des vérifications null défensives pour empêcher ces allocateurs anciens provoque un arrêt immédiat en cas d’échec. Le **/Zc:throwingNew** option indique au compilateur d’ignorer ces vérifications null, en supposant que tous les liés mémoire allocateurs conforme à la norme. Cela ne s’applique pas à non lanceurs explicite `operator new` surcharges, qui sont déclarées à l’aide d’un paramètre supplémentaire de type `std::nothrow_t` et explicite `noexcept` spécification.

Point de vue conceptuel, pour créer un objet sur le magasin libre, le compilateur génère du code pour allouer la mémoire, puis à appeler son constructeur pour initialiser la mémoire. Étant donné que le compilateur Visual C++ normalement ne peut pas déterminer si ce code sera lié à un allocateur non conforme, non lanceurs, par défaut il génère également une vérification de valeur null avant d’appeler le constructeur. Cela empêche un pointeur null dans l’appel de constructeur de déréférencer si une allocation non lanceurs échoue. Dans la plupart des cas, ces contrôles ne sont pas nécessaires, car la valeur par défaut `operator new` allocateurs lever au lieu de retourner des pointeurs null. Les vérifications ont également fâcheux effets secondaires. Ils et Active la taille du code, ils illuminer PRÉDICTEUR de branche et ils ce qui affecterait les autres optimisations du compilateur utiles telles que devirtualization ou const propagation hors de l’objet initialisé. Les vérifications existent uniquement au code de prise en charge des liens vers *nothrownew.obj* ou non conformes personnalisé `operator new` implémentations. Si vous n’utilisez pas la non conformes `operator new`, nous vous recommandons d’utiliser **/Zc:throwingNew** pour optimiser votre code.

Le **/Zc:throwingNew** option est désactivée par défaut et n’est pas affectée par la [/ permissive-](permissive-standards-conformance.md) option.

Si vous compilez à l’aide de la génération de code de l’édition de liens (LTCG), vous n’avez pas besoin de spécifier **/Zc:throwingNew**. Lorsque votre code est compilé à l’aide de /LTCG, le compilateur peut détecter si la valeur par défaut, conforme `operator new` implémentation est utilisée. Dans ce cas, le compilateur laisse automatiquement les contrôles de valeur null. L’éditeur de liens recherche le **/ThrowingNew** indicateur servant à déterminer si l’implémentation de `operator new` est conforme. Vous pouvez spécifier cet indicateur pour l’éditeur de liens en incluant cette directive dans la source de votre implémentation de nouvel opérateur personnalisé :

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. À partir de la **Configuration** menu déroulant, choisissez **toutes les Configurations**.

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier la **des Options supplémentaires** propriété à inclure **/Zc:throwingNew** ou **/Zc:throwingNew-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Spécifications d’exception (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Arrêter (exception)](../../standard-library/exception-functions.md#terminate)<br/>
