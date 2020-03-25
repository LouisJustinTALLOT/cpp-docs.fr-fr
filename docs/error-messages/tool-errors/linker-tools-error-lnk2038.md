---
title: Erreur des outils Éditeur de liens LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 45078d8e1bdbeb23dd311d915ba2cf47e42b2663
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194510"
---
# <a name="linker-tools-error-lnk2038"></a>Erreur des outils Éditeur de liens LNK2038

> incompatibilité détectée pour'*Name*' : la valeur'*value_1*'ne correspond pas à la valeur'*Value_2*'dans *filename. obj*

Une incompatibilité de symbole a été détectée par l'éditeur de liens. Cette erreur indique que les différentes parties d’une application, y compris les bibliothèques ou tout autre code objet lié par l’application, utilisent des définitions conflictuelles du symbole. Le pragma de [détection de discordance](../../preprocessor/detect-mismatch.md) est utilisé pour définir ces symboles et détecter leurs valeurs conflictuelles.

## <a name="possible-causes-and-solutions"></a>Causes et solutions possibles

Cette erreur peut se produire lorsqu'un fichier objet de votre projet est obsolète. Avant d'essayer d'autres solutions pour résoudre cette erreur, exécutez une build propre pour vérifier que les fichiers objets sont actualisés.

Visual Studio définit les symboles ci-dessous pour empêcher la liaison du code incompatible, qui peut provoquer des erreurs d'exécution ou d'autres comportements inattendus.

- `_MSC_VER` indique les numéros de version principale et secondaire du compilateur C++ Microsoft (MSVC) utilisé pour générer une application ou une bibliothèque. Le code compilé à l’aide d’une version de MSVC est incompatible avec le code compilé à l’aide d’une version dont les numéros de version principale et secondaire sont différents. Pour plus d’informations, consultez `_MSC_VER` dans les [macros prédéfinies](../../preprocessor/predefined-macros.md).

   Si vous établissez une liaison à une bibliothèque qui n’est pas compatible avec la version de MSVC que vous utilisez, et que vous ne pouvez pas acquérir ou générer une version compatible de la bibliothèque, vous pouvez utiliser une version antérieure du compilateur pour générer votre projet : remplacez la propriété **ensemble d’outils de plateforme** du projet par l’ensemble d’outils précédent. Pour plus d’informations, consultez [Comment : modifier le Framework cible et l’ensemble d’outils de plateforme](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL` indique le niveau de sécurité et les fonctionnalités de débogage qui sont activées C++ dans la bibliothèque standard. Ces fonctionnalités peuvent modifier la représentation de certains objets de la bibliothèque C++ standard et ainsi les rendre incompatibles avec ceux qui utilisent d’autres fonctionnalités de sécurité et de débogage. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary` indique la version de la C++ bibliothèque standard et du runtime C qui est utilisé par une application ou une bibliothèque. Le code qui utilise une version de la bibliothèque standard C++ ou de la bibliothèque Runtime C est incompatible avec le code qui utilise une autre version. Pour plus d’informations, consultez l’article [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT` indique que le code qui utilise la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) est lié aux objets compilés à l’aide d’un paramètre différent pour l’option de compilateur [/ZW](../../build/reference/zw-windows-runtime-compilation.md) . ( **/ZW** prend C++en charge/CX.) Le code qui utilise ou dépend de la bibliothèque PPL doit être compilé à l’aide du même paramètre **/ZW** utilisé dans le reste de l’application.

Assurez-vous que les valeurs de ces symboles soient cohérentes dans tous les projets de votre solution Visual Studio, et aussi qu'elles soient compatibles avec le code et les bibliothèques auxquels votre application est liée.

## <a name="third-party-library-issues-and-vcpkg"></a>Problèmes de bibliothèque tierce et vcpkg

Si vous voyez cette erreur lorsque vous essayez de configurer une bibliothèque tierce dans le cadre de votre Build, envisagez d’utiliser [vcpkg](../../vcpkg.md), le C++ gestionnaire de package Visual pour installer et générer la bibliothèque. Vcpkg prend en charge une liste volumineuse et croissante [de bibliothèques tierces](https://github.com/Microsoft/vcpkg/tree/master/ports), et définit toutes les propriétés de configuration et les dépendances requises pour les builds réussies dans le cadre de votre projet. Pour plus d’informations, consultez le billet de [blog visuel C++ ](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) associé.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
