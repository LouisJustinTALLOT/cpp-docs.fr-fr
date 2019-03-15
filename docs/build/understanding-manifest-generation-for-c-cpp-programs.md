---
title: Fonctionnement de la génération de manifestes pour les programmes C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: ff8d9f214b4fe4d004691c54474dcdabf2c0af85
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807349"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Fonctionnement de la génération de manifestes pour les programmes C/C++

Un [manifeste](/windows/desktop/sbscs/manifests) est un document XML qui peut être un fichier XML externe ou une ressource incorporé dans une application ou un assembly. Le manifeste d’un [application isolée](/windows/desktop/SbsCs/isolated-applications) est utilisé pour gérer les noms et les versions des assemblys côte à côte partagés auxquels l’application doit se lier au moment de l’exécution. Le manifeste d’un assembly côte à côte spécifie ses dépendances sur les noms, les versions, les ressources et les autres assemblys.

Il existe deux façons de créer un manifeste pour une application isolée ou un assembly côte à côte. Tout d’abord, l’auteur de l’assembly peut créer manuellement un fichier de manifeste suivant les règles et conventions de dénomination. Vous pouvez également, si un programme dépend uniquement des assemblys Visual C++ telles que la bibliothèque CRT, MFC, ATL ou d’autres, un manifeste peut être généré automatiquement par l’éditeur de liens.

Les en-têtes de bibliothèques Visual C++ contiennent des informations de l’assembly, et lorsque les bibliothèques sont incluses dans le code d’application, ces informations d’assembly sont utilisées par l’éditeur de liens pour former un manifeste pour le fichier binaire final. L’éditeur de liens n’incorpore pas le fichier manifeste dans le fichier binaire et ne peut générer le manifeste comme un fichier externe. Avoir un manifeste comme un fichier externe peut ne pas fonctionne pour tous les scénarios. Par exemple, il est recommandé que les assemblys privés aient des manifestes incorporés. Dans les versions de ligne de commande telles que celles qui utilisent nmake pour générer du code, un manifeste peut être incorporé à l’aide de l’outil manifeste. Pour plus d’informations, consultez [génération de manifeste à la ligne de commande](manifest-generation-at-the-command-line.md). Lors de la génération dans Visual Studio, vous pouvez incorporer un manifeste en définissant une propriété pour l’outil manifeste dans le **propriétés du projet** boîte de dialogue, consultez [génération de manifeste dans Visual Studio](manifest-generation-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

[Concepts d’applications isolées et d’assemblys côte à côte](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Génération d’applications isolées et d’assemblys côte à côte C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
