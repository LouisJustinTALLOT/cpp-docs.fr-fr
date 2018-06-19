---
title: Technologie active et DLL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5e0296b994f7944d5b26e98ba1b0545a03ec55b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360111"
---
# <a name="active-technology-and-dlls"></a>Technologie active et DLL
Technologie active permet de serveurs d’objets à mettre en œuvre entièrement à l’intérieur d’une DLL. Ce type de serveur est appelé serveur in-process. MFC ne gère pas complètement les serveurs in-process pour toutes les fonctionnalités d’édition, essentiellement parce que la technologie Active ne fournit pas un moyen pour un serveur de se connecter à la boucle de messages principale du conteneur. MFC requiert l’accès à la boucle de message de l’application conteneur pour gérer les touches d’accès et le traitement des temps d’inactivité.  
  
 Si vous écrivez un serveur Automation et que votre serveur ne dispose pas d’interface utilisateur, vous pouvez rendre votre serveur un serveur in-process et l’intégrer complètement dans une DLL.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Serveurs Automation](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DLL dans Visual C++](../build/dlls-in-visual-cpp.md)