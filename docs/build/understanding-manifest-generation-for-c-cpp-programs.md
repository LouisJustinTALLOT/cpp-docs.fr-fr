---
title: Comprendre la génération de manifestes pour les programmes C/C++ | Microsoft Docs
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
ms.openlocfilehash: 40dbc61009cdfaa5621335cfb78dd10eae2138ca
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572066"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Fonctionnement de la génération de manifestes pour les programmes C/C++
Un [manifeste](http://msdn.microsoft.com/library/aa375365) est un document XML qui peut être un fichier XML externe ou une ressource incorporé dans une application ou un assembly. Le manifeste d’un [application isolée](http://msdn.microsoft.com/library/aa375190) est utilisé pour gérer les noms et les versions des assemblys côte à côte partagés auxquels l’application doit se lier au moment de l’exécution. Le manifeste d’un assembly côte à côte spécifie ses dépendances sur les noms, les versions, les ressources et les autres assemblys.  
  
 Il existe deux façons de créer un manifeste pour une application isolée ou un assembly côte à côte. Tout d’abord, l’auteur de l’assembly peut créer manuellement un fichier de manifeste suivant les règles et conventions de dénomination. Vous pouvez également, si un programme dépend uniquement des assemblys Visual C++ telles que la bibliothèque CRT, MFC, ATL ou d’autres, un manifeste peut être généré automatiquement par l’éditeur de liens.  
  
 Les en-têtes de bibliothèques Visual C++ contiennent des informations de l’assembly, et lorsque les bibliothèques sont incluses dans le code d’application, ces informations d’assembly sont utilisées par l’éditeur de liens pour former un manifeste pour le fichier binaire final. L’éditeur de liens n’incorpore pas le fichier manifeste dans le fichier binaire et ne peut générer le manifeste comme un fichier externe. Avoir un manifeste comme un fichier externe peut ne pas fonctionne pour tous les scénarios. Par exemple, il est recommandé que les assemblys privés aient des manifestes incorporés. Dans les versions de ligne de commande telles que celles qui utilisent nmake pour générer du code, un manifeste peut être incorporé à l’aide de l’outil manifeste. Pour plus d’informations, consultez [génération de manifeste à la ligne de commande](../build/manifest-generation-at-the-command-line.md). Lors de la génération dans Visual Studio, vous pouvez incorporer un manifeste en définissant une propriété pour l’outil manifeste dans le **propriétés du projet** boîte de dialogue, consultez [génération de manifeste dans Visual Studio](../build/manifest-generation-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts d’Applications isolées et assemblys côte à côte](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Génération d’applications isolées et d’assemblys côte à côte C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)