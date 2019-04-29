---
title: '/ Zc : threadsafeinit (initialisation statique locale thread-safe)'
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
ms.openlocfilehash: 92a1bfa5ec3bab2814397d51e35e617b7666c706
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315701"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/ Zc : threadsafeinit (initialisation statique locale thread-safe)

Le **/Zc : threadsafeinit** option du compilateur indique au compilateur pour initialiser les variables locales statiques (portée de fonction) de façon thread-safe, éliminant la nécessité d’une synchronisation manuelle. Uniquement l’initialisation est thread-safe. Utilisation et modification de variables locales statiques par plusieurs threads doivent être synchronisées manuellement. Cette option est disponible à partir de Visual Studio 2015. Par défaut, Visual Studio active cette option.

## <a name="syntax"></a>Syntaxe

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>Notes

Dans la norme C ++ 11, variables de portée de bloc avec statique ou une durée de stockage thread doit être initialisé à zéro avant toute autre initialisation a lieu. L’initialisation se produit lorsque le contrôle passe tout d’abord par la déclaration de la variable. Si une exception est levée pendant l’initialisation, la variable est considéré comme non initialisées, et l’initialisation est tentée de nouveau le contrôle de temps suivant passe par la déclaration. Si le contrôle pénètre dans la déclaration en même temps que l’initialisation, les blocs de l’exécution simultanée, tandis que l’initialisation est terminée. Le comportement est indéfini si le contrôle revient dans la déclaration de manière récursive pendant l’initialisation. Par défaut, Visual Studio à partir de Visual Studio 2015 implémente ce comportement standard. Ce comportement peut être spécifié explicitement en définissant le **/Zc : threadsafeinit** option du compilateur.

Le **/Zc : threadsafeinit** option du compilateur est activée par défaut. Le [/ permissive-](permissive-standards-conformance.md) option n’affecte pas **/Zc : threadsafeinit**.

Initialisation thread-safe de variables locales statiques s’appuie sur le code implémenté dans la bibliothèque de runtime C universel (UCRT). Pour éviter une dépendance sur la bibliothèque UCRT, ou pour conserver le comportement de l’initialisation thread-safe des versions de Visual Studio antérieures à Visual Studio 2015, utilisez le **/Zc:threadSafeInit-** option. Si vous savez que la sécurité des threads n’est pas nécessaire, utilisez cette option pour générer un code légèrement plus petit et plus rapide autour des déclarations locales statiques.

Les variables locales statiques thread-safe utilisent le stockage local des threads (TLS) en interne pour fournir une exécution efficace lorsque la méthode statique a déjà été initialisée. L’implémentation de cette fonctionnalité s’appuie sur les fonctions de prise en charge de système d’exploitation Windows dans Windows Vista et les systèmes d’exploitation ultérieurs. Windows XP, Windows Server 2003 et des systèmes d’exploitation plus anciens n’ont pas cette prise en charge, afin qu’ils n’obtiennent pas l’avantage de l’efficacité. Ces systèmes d’exploitation ont également une limite inférieure sur le nombre de sections TLS qui peuvent être chargées. Dépassement le TLS limite de section peut provoquer un incident. S’il s’agit d’un problème dans votre code, en particulier dans le code qui doit s’exécuter sur les systèmes d’exploitation plus anciens, utilisez **/Zc:threadSafeInit-** pour désactiver le code d’initialisation thread-safe.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. À partir de la **Configurations** menu déroulant, choisissez **toutes les Configurations**.

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc : threadsafeinit** ou **/Zc:threadSafeInit-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>
