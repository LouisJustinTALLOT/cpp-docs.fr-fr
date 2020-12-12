---
description: 'En savoir plus sur:/Zc : threadSafeInit (initialisation statique locale thread-safe)'
title: '/Zc : threadSafeInit (initialisation statique locale thread-safe)'
ms.date: 03/14/2018
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
ms.openlocfilehash: ac14e7979d2adab0b21229f426e00a489c14f38f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271211"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc : threadSafeInit (initialisation statique locale thread-safe)

L’option de compilateur **/Zc : threadSafeInit** indique au compilateur d’initialiser les variables locales statiques (portée de fonction) de façon thread-safe, ce qui évite d’avoir à effectuer une synchronisation manuelle. Seule l’initialisation est thread-safe. L’utilisation et la modification de variables locales statiques par plusieurs threads doivent tout de même être synchronisées manuellement. Cette option est disponible à partir de Visual Studio 2015. Par défaut, Visual Studio active cette option.

## <a name="syntax"></a>Syntaxe

> **/Zc : threadSafeInit**[ **-** ]

## <a name="remarks"></a>Notes

Dans la norme C++ 11, les variables de portée de bloc avec une durée de stockage statique ou de thread doivent être initialisées à zéro avant que toute autre initialisation n’ait lieu. L’initialisation se produit lorsque le contrôle passe d’abord par la déclaration de la variable. Si une exception est levée pendant l’initialisation, la variable est considérée comme non initialisée, et l’initialisation est tentée à nouveau la prochaine fois que le contrôle passe par la déclaration. Si le contrôle entre dans la déclaration simultanément avec l’initialisation, les blocs d’exécution simultanés pendant l’initialisation sont terminés. Le comportement n’est pas défini si le contrôle accède à nouveau à la déclaration de manière récursive pendant l’initialisation. Par défaut, Visual Studio à partir de Visual Studio 2015 implémente ce comportement standard. Ce comportement peut être explicitement spécifié en définissant l’option de compilateur **/Zc : threadSafeInit** .

L’option de compilateur **/Zc : threadSafeInit** est activée par défaut. L’option [/permissive-](permissive-standards-conformance.md) n’a pas d’incidence sur **/Zc : threadSafeInit**.

L’initialisation thread-safe des variables locales statiques s’appuie sur le code implémenté dans la bibliothèque Runtime C universelle (UCRT). Pour éviter d’avoir une dépendance sur le UCRT ou de conserver le comportement d’initialisation non thread-safe des versions de Visual Studio antérieures à Visual Studio 2015, utilisez l’option **/Zc : threadSafeInit-** . Si vous savez que la sécurité des threads n’est pas requise, utilisez cette option pour générer un code légèrement plus petit et plus rapide autour des déclarations locales statiques.

Les variables locales statiques thread-safe utilisent le stockage local des threads (TLS) en interne pour fournir une exécution efficace lorsque la statique a déjà été initialisée. L’implémentation de cette fonctionnalité s’appuie sur les fonctions de prise en charge du système d’exploitation Windows dans Windows Vista et les systèmes d’exploitation ultérieurs. Windows XP, Windows Server 2003 et les systèmes d’exploitation plus anciens ne bénéficient pas de cette prise en charge. ils ne bénéficient donc pas de l’avantage de l’efficacité. Ces systèmes d’exploitation ont également une limite inférieure sur le nombre de sections TLS qui peuvent être chargées. Le dépassement de la limite de la section TLS peut entraîner un blocage. S’il s’agit d’un problème dans votre code, en particulier dans le code qui doit s’exécuter sur des systèmes d’exploitation plus anciens, utilisez **/Zc : threadSafeInit-** pour désactiver le code d’initialisation thread-safe.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le menu déroulant **configurations** , choisissez **toutes les configurations**.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **options supplémentaires** pour inclure **/Zc : threadSafeInit** ou **/Zc : ThreadSafeInit-** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>
