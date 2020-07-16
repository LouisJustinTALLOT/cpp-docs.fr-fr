---
title: Erreur des outils Éditeur de liens LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 69a832716dffee4e024b3bb1a1f0de6ee8105e99
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404162"
---
# <a name="linker-tools-error-lnk2038"></a>Erreur des outils Éditeur de liens LNK2038

> incompatibilité détectée pour'*Name*' : la valeur'*value_1*'ne correspond pas à la valeur'*Value_2*'dans *filename. obj*

Une incompatibilité de symbole a été détectée par l'éditeur de liens. Cette erreur indique que les différentes parties d’une application, y compris les bibliothèques ou tout autre code objet lié par l’application, utilisent des définitions conflictuelles du symbole. Le pragma de [détection de discordance](../../preprocessor/detect-mismatch.md) est utilisé pour définir ces symboles et détecter leurs valeurs conflictuelles.

## <a name="possible-causes-and-solutions"></a>Causes et solutions possibles

Cette erreur peut se produire lorsqu'un fichier objet de votre projet est obsolète. Avant d'essayer d'autres solutions pour résoudre cette erreur, exécutez une build propre pour vérifier que les fichiers objets sont actualisés.

Visual Studio définit les symboles ci-dessous pour empêcher la liaison du code incompatible, qui peut provoquer des erreurs d'exécution ou d'autres comportements inattendus.

- `_MSC_VER`Indique les numéros de version principale et secondaire du compilateur Microsoft C++ (MSVC) utilisé pour générer une application ou une bibliothèque. Le code compilé à l’aide d’une version de MSVC est incompatible avec le code compilé à l’aide d’une version dont les numéros de version principale et secondaire sont différents. Pour plus d’informations, consultez `_MSC_VER` dans les [macros prédéfinies](../../preprocessor/predefined-macros.md).

   Si vous établissez une liaison à une bibliothèque qui n’est pas compatible avec la version de MSVC que vous utilisez, et que vous ne pouvez pas acquérir ou générer une version compatible de la bibliothèque, vous pouvez utiliser une version antérieure du compilateur pour générer votre projet : remplacez la propriété **ensemble d’outils de plateforme** du projet par l’ensemble d’outils précédent. Pour plus d’informations, consultez [Comment : modifier le Framework cible et l’ensemble d’outils de plateforme](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL`Indique le niveau de sécurité et les fonctionnalités de débogage qui sont activées dans la bibliothèque C++ standard. Ces fonctionnalités peuvent modifier la représentation de certains objets de la bibliothèque C++ standard et ainsi les rendre incompatibles avec ceux qui utilisent d’autres fonctionnalités de sécurité et de débogage. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary`Indique la version de la bibliothèque standard C++ et du runtime C qui est utilisé par une application ou une bibliothèque. Le code qui utilise une version de la bibliothèque standard C++ ou de la bibliothèque Runtime C est incompatible avec le code qui utilise une autre version. Pour plus d’informations, consultez l’article [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT`Indique que le code qui utilise la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) est lié aux objets compilés à l’aide d’un paramètre différent pour l’option de compilateur [/ZW](../../build/reference/zw-windows-runtime-compilation.md) . (**/ZW** prend en charge C++/CX.) Le code qui utilise ou dépend de la bibliothèque PPL doit être compilé à l’aide du même paramètre **/ZW** utilisé dans le reste de l’application.

Assurez-vous que les valeurs de ces symboles soient cohérentes dans tous les projets de votre solution Visual Studio, et aussi qu'elles soient compatibles avec le code et les bibliothèques auxquels votre application est liée.

## <a name="third-party-library-issues-and-vcpkg"></a>Problèmes de bibliothèque tierce et vcpkg

Si vous voyez cette erreur lorsque vous essayez de configurer une bibliothèque tierce dans le cadre de votre Build, envisagez d’utiliser [vcpkg](../../vcpkg.md), un gestionnaire de package C++, pour installer et générer la bibliothèque. vcpkg prend en charge une liste volumineuse et croissante [de bibliothèques tierces](https://github.com/Microsoft/vcpkg/tree/master/ports), et définit toutes les propriétés de configuration et les dépendances requises pour les builds réussies dans le cadre de votre projet.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
