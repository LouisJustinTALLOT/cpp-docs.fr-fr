---
title: Erreur des LNK2038 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2038
dev_langs:
- C++
helpviewer_keywords:
- LNK2038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f97f65bbe31e51e5083b34949b47a6963696ee37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301666"
---
# <a name="linker-tools-error-lnk2038"></a>Erreur des outils Éditeur de liens LNK2038

> Discordance détectée pour '*nom*' : valeur '*value_1*'ne correspond pas à valeur'*value_2*' dans *filename.obj*

Une incompatibilité de symbole a été détectée par l'éditeur de liens. Cette erreur indique que différentes parties d’une application, y compris les bibliothèques ou tout autre objet de code que les liens de l’application, utilisent des définitions incompatibles du symbole. Le [détecter incompatibilité](../../preprocessor/detect-mismatch.md) pragma est utilisé pour définir ces symboles et détecter leurs valeurs en conflit.

## <a name="possible-causes-and-solutions"></a>Causes et solutions possibles

Cette erreur peut se produire lorsqu'un fichier objet de votre projet est obsolète. Avant d'essayer d'autres solutions pour résoudre cette erreur, exécutez une build propre pour vérifier que les fichiers objets sont actualisés.

Visual Studio définit les symboles ci-dessous pour empêcher la liaison du code incompatible, qui peut provoquer des erreurs d'exécution ou d'autres comportements inattendus.

- `_MSC_VER`  
   Indique les numéros de version principale et secondaire du compilateur Visual C++ utilisé pour générer une application ou une bibliothèque. Le code compilé à l'aide d'une version du compilateur Visual C++ est incompatible avec le code compilé à l'aide d'une version comportant des numéros de version principale et secondaire différents. Pour plus d’informations, consultez `_MSC_VER` dans [Macros prédéfinies](../../preprocessor/predefined-macros.md).

   Si vous créez un lien vers une bibliothèque qui n’est pas compatible avec la version du compilateur Visual C++ que vous utilisez, et vous ne peut pas acquérir ou générer une version compatible de la bibliothèque, vous pouvez utiliser une version antérieure du compilateur pour générer votre projet : modifier le <C1/>outils de plateforme** propriété du projet à l’ensemble d’outils antérieur. Pour plus d’informations, consultez [Comment : modifier le Framework cible et un ensemble d’outils de plateforme](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL`  
   Indique le niveau de sécurité et les fonctionnalités de débogage activés dans la bibliothèque standard C++. Ces fonctionnalités peuvent modifier la représentation de certains objets de la bibliothèque C++ standard et ainsi les rendre incompatibles avec ceux qui utilisent d’autres fonctionnalités de sécurité et de débogage. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary`  
   Indique la version de la bibliothèque standard C++ ou de la bibliothèque Runtime C utilisée par une application ou une bibliothèque. Le code qui utilise une version de la bibliothèque standard C++ ou de la bibliothèque Runtime C est incompatible avec le code qui utilise une autre version. Pour plus d’informations, consultez l’article [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT`  
   Indique que le code qui utilise le [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) est lié aux objets compilés à l’aide d’un autre paramètre pour le [/ZW](../../build/reference/zw-windows-runtime-compilation.md) option du compilateur. (**/ZW** prend en charge C + c++ / CX.) Code qui utilise ou dépend de la bibliothèque PPL doit être compilé à l’aide de la même **/ZW** qui est utilisée dans le reste de l’application.

Assurez-vous que les valeurs de ces symboles soient cohérentes dans tous les projets de votre solution Visual Studio, et aussi qu'elles soient compatibles avec le code et les bibliothèques auxquels votre application est liée.

## <a name="third-party-library-issues-and-vcpkg"></a>Problèmes de bibliothèque tierce et Vcpkg

Si vous recevez cette erreur lorsque vous essayez de configurer une bibliothèque tierce dans le cadre de votre build, envisagez d’utiliser [Vcpkg](../../vcpkg.md), le Gestionnaire de Package Visual C++, pour installer et de générer la bibliothèque. Prend en charge Vcpkg important et croissant [la liste des bibliothèques tierces](https://github.com/Microsoft/vcpkg/tree/master/ports)et définit toutes les propriétés de configuration et les dépendances requises pour les générations réussies dans le cadre de votre projet. Pour plus d’informations, consultez le [Blog Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) valider.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)