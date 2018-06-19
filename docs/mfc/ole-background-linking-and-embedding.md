---
title: 'Arrière-plan OLE : Liaison et incorporation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5dc7a5770c98323187dbabcd8c2a7bb9eb652de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347277"
---
# <a name="ole-background-linking-and-embedding"></a>Arrière-plan OLE : liaison et incorporation
À l’aide de la commande Coller dans une application conteneur peut créer un composant incorporé ou un élément incorporé. Les données sources pour un élément incorporé sont stockées en tant que partie du document OLE qui le contient. De cette façon, un fichier de document pour un document de traitement de texte peut contenir du texte et peut également contenir les bitmaps, des graphiques, des formules ou tout autre type de données.  
  
 OLE fournit une autre façon d’intégrer des données d’une autre application : création d’un composant lié, ou élément lié ou un lien. Les étapes de création d’un élément lié sont similaires à ceux de la création d’un élément incorporé, à ceci près que vous utilisez la commande Coller la liaison au lieu de la commande Coller. Contrairement à un composant incorporé, un composant lié stocke un chemin d’accès aux données d’origine, ce qui est souvent dans un fichier distinct.  
  
 Par exemple, si vous travaillez dans un mot document du processeur et créez un élément lié à des cellules de feuille de calcul, les données pour l’élément lié sont stockées dans le document de feuille de calcul d’origine. Le document de traitement de texte contient uniquement les informations indiquant où l’élément se trouve, autrement dit, il contient un lien vers le document de feuille de calcul d’origine. Lorsque vous double-cliquez sur les cellules, lancement de l’application de la feuille de calcul et le document d’origine de la feuille de calcul est chargé à partir de l’emplacement de stockage.  
  
 Chaque élément OLE, si incorporé ou lié, a un type en fonction de l’application qui l’a créé est associé. Par exemple, un élément Microsoft Paintbrush est un type d’élément et un élément de Microsoft Excel est un autre type. Certaines applications, toutefois, peuvent créer plusieurs types d’élément. Par exemple, Microsoft Excel peut créer des éléments de la feuille de calcul, des éléments de graphique et des éléments feuille macro. Chacun de ces éléments peut être identifiée par le système à l’aide d’un identificateur de classe ou **CLSID**.  
  
## <a name="see-also"></a>Voir aussi  
 [Arrière-plan OLE](../mfc/ole-background.md)   
 [Arrière-plan OLE : Conteneurs et serveurs](../mfc/ole-background-containers-and-servers.md)   
 [Conteneurs : Éléments clients](../mfc/containers-client-items.md)   
 [Serveurs : éléments du serveur](../mfc/servers-server-items.md)

