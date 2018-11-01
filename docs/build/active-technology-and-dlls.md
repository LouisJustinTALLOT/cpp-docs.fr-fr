---
title: Technologie active et DLL
ms.date: 11/04/2016
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
ms.openlocfilehash: 270c64df9af792a73acf1ad408aca02e7fadc30f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535809"
---
# <a name="active-technology-and-dlls"></a>Technologie active et DLL

Technologie active permet de serveurs d’objets à mettre en œuvre entièrement à l’intérieur d’une DLL. Ce type de serveur est appelé un serveur in-process. MFC ne pas complètement prend en charge les serveurs intra-processus pour toutes les fonctionnalités d’édition, principalement parce que la technologie Active ne fournit pas un moyen pour un serveur auquel se raccorder la boucle de messages principale du conteneur. MFC requiert l’accès à la boucle de message de l’application conteneur pour gérer les touches d’accès rapide et traitement des temps d’inactivité.

Si vous écrivez un serveur Automation et que votre serveur ne dispose pas d’interface utilisateur, vous pouvez rendre votre serveur un serveur in-process et l’intégrer complètement dans une DLL.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Serveurs Automation](../mfc/automation-servers.md)

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)