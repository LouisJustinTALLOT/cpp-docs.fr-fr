---
title: 'Arrière-plan OLE : Liaison et incorporation'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
ms.openlocfilehash: 02607df2a8fa086c5751f2b446e349a3efdbcd20
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280964"
---
# <a name="ole-background-linking-and-embedding"></a>Arrière-plan OLE : Liaison et incorporation

À l’aide de la commande Coller dans une application conteneur peut créer un composant incorporé ou un élément incorporé. Les données sources pour un élément incorporé sont stockées en tant que partie du document OLE qui le contient. De cette façon, un fichier de document pour un document de traitement de texte peut contenir du texte et peut également contenir les bitmaps, graphiques, formules ou tout autre type de données.

OLE fournit une autre façon d’incorporer des données à partir d’une autre application : création d’un composant lié, ou élément lié ou un lien. Les étapes de création d’un élément lié sont similaires à celles permettant de créer un élément incorporé, excepté que vous utilisez la commande Coller la liaison au lieu de la commande Coller. Contrairement à un composant incorporé, un composant lié stocke un chemin d’accès aux données d’origine, ce qui est souvent dans un fichier distinct.

Par exemple, si vous travaillez dans un mot document de processeur et créez un élément lié à certaines cellules de feuille de calcul, les données pour l’élément lié sont stockées dans le document de feuille de calcul d’origine. Le document de traitement de texte contient uniquement les informations spécifiant où l’élément peut être trouvé, autrement dit, il contient un lien vers le document de feuille de calcul d’origine. Lorsque vous double-cliquez sur les cellules, lancement de l’application de feuille de calcul et le document de feuille de calcul d’origine est chargé à partir de l’emplacement de stockage.

Chaque élément OLE, si incorporé ou lié, a un type basé sur l’application qui l’a créée. Par exemple, un élément Microsoft Paintbrush est un type d’élément et un élément de Microsoft Excel est un autre type. Certaines applications, toutefois, peuvent créer plusieurs types d’élément. Par exemple, Microsoft Excel peut créer des éléments de la feuille de calcul, des éléments de graphique et des éléments feuille macro. Chacun de ces éléments peut être identifiée par le système à l’aide d’un identificateur de classe ou **CLSID**.

## <a name="see-also"></a>Voir aussi

[Arrière-plan OLE](../mfc/ole-background.md)<br/>
[Arrière-plan OLE : Conteneurs et les serveurs](../mfc/ole-background-containers-and-servers.md)<br/>
[Conteneurs : Éléments clients](../mfc/containers-client-items.md)<br/>
[serveurs : Éléments de serveur](../mfc/servers-server-items.md)
