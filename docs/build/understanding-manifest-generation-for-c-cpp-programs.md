---
title: Fonctionnement de la génération de manifestes pour les programmes C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492524"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Fonctionnement de la génération de manifestes pour les programmes C/C++

Un [manifeste](/windows/win32/sbscs/manifests) est un document XML qui peut être un fichier XML externe ou une ressource incorporée dans une application ou un assembly. Le manifeste d’une [application isolée](/windows/win32/SbsCs/isolated-applications) est utilisé pour gérer les noms et les versions des assemblys partagés côte à côte auxquels l’application doit se lier au moment de l’exécution. Le manifeste d’un assembly côte à côte spécifie ses dépendances sur les noms, les versions, les ressources et d’autres assemblys.

Il existe deux façons de créer un manifeste pour une application isolée ou un assembly côte à côte. Tout d’abord, l’auteur de l’assembly peut créer manuellement un fichier manifeste en suivant les règles et les spécifications de nommage. Sinon, si un programme dépend uniquement d’assemblys visuels C++ tels que CRT, MFC, ATL ou d’autres, un manifeste peut être généré automatiquement par l’éditeur de liens.

Les en-têtes de C++ bibliothèques visuelles contiennent des informations d’assembly et, lorsque les bibliothèques sont incluses dans le code d’application, ces informations d’assembly sont utilisées par l’éditeur de liens pour former un manifeste pour le binaire final. L’éditeur de liens n’incorpore pas le fichier manifeste dans le fichier binaire et ne peut générer le manifeste qu’en tant que fichier externe. Le fait de disposer d’un manifeste en tant que fichier externe peut ne pas fonctionner pour tous les scénarios. Par exemple, il est recommandé que les assemblys privés aient des manifestes incorporés. Dans les builds de ligne de commande telles que celles qui utilisent NMAKE pour générer le code, un manifeste peut être incorporé à l’aide de l’outil manifeste. Pour plus d’informations, consultez [génération de manifeste à partir de la ligne de commande](manifest-generation-at-the-command-line.md). Lors de la génération dans Visual Studio, un manifeste peut être incorporé en définissant une propriété pour l’outil manifeste dans la boîte de dialogue **Propriétés du projet** . consultez [génération de manifeste dans Visual Studio](manifest-generation-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

[Concepts d’applications isolées et d’assemblys côte à côte](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Génération d’applications isolées et d’assemblys côte à côte C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
