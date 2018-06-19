---
title: Présentation de génération de manifeste pour les programmes C/C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb6a65c718b88e4072c0ddad19411bb8ea4ddcff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381625"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Fonctionnement de la génération de manifestes pour les programmes C/C++
A [manifeste](http://msdn.microsoft.com/library/aa375365) est un document XML qui peut être un fichier XML externe ou une ressource incorporé dans une application ou un assembly. Le manifeste d’un [application isolée](http://msdn.microsoft.com/library/aa375190) est utilisé pour gérer les noms et les versions des assemblys côte à côte partagés auxquels l’application doit se lier au moment de l’exécution. Le manifeste d’un assembly côte à côte spécifie ses dépendances sur les noms, des versions, des ressources et des autres assemblys.  
  
 Il existe deux façons de créer un manifeste pour une application isolée ou un assembly côte à côte. Tout d’abord, l’auteur de l’assembly peut créer manuellement un fichier manifeste en suivant les règles et les exigences d’affectation de noms. Vous pouvez également, si un programme dépend uniquement des assemblys Visual C++ telles que CRT, MFC, ATL ou d’autres, un manifeste peut être généré automatiquement par l’éditeur de liens.  
  
 Les en-têtes des bibliothèques Visual C++ contiennent des informations de l’assembly, et lorsque les bibliothèques sont incluses dans le code d’application, ces informations d’assembly sont utilisées par l’éditeur de liens pour former un manifeste pour le fichier binaire final. L’éditeur de liens n’incorpore pas le fichier manifeste dans le fichier binaire et ne peut générer le manifeste comme un fichier externe. Ayant un manifeste pour un fichier externe peut ne pas fonctionne pour tous les scénarios. Par exemple, il est recommandé que les assemblys privés aient des manifestes incorporés. Dans les versions de ligne de commande telles que celles qui utilisent nmake pour générer le code, un manifeste peut être incorporé à l’aide de l’outil manifeste. Pour plus d’informations, consultez [génération de manifeste à la ligne de commande](../build/manifest-generation-at-the-command-line.md). Lors de la génération [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], un manifeste peut être incorporé en définissant une propriété pour l’outil manifeste dans le **propriétés du projet** boîte de dialogue, consultez [génération de manifeste dans Visual Studio](../build/manifest-generation-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts d’Applications isolées et les assemblys côte à côte](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Génération d’applications isolées et d’assemblys côte à côte C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)