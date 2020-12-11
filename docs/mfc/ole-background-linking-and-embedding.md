---
description: 'En savoir plus sur : arrière-plan OLE : liaison et incorporation'
title: 'Arrière-plan OLE : liaison et incorporation'
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
ms.openlocfilehash: 05bd51c11cadfc3220f23db9098db9f07703a814
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112217"
---
# <a name="ole-background-linking-and-embedding"></a>Arrière-plan OLE : liaison et incorporation

L’utilisation de la commande coller dans une application conteneur peut créer un composant incorporé, ou un élément incorporé. Les données sources d’un élément incorporé sont stockées dans le cadre du document OLE qui le contient. De cette façon, un fichier de document pour un document de traitement de texte peut contenir du texte et peut également contenir des bitmaps, des graphiques, des formules ou tout autre type de données.

OLE offre une autre façon d’incorporer des données à partir d’une autre application : créer un composant lié, un élément lié ou un lien. Les étapes de création d’un élément lié sont similaires à celles de la création d’un élément incorporé, à la différence près que vous utilisez la commande Coller le lien au lieu de la commande Coller. Contrairement à un composant incorporé, un composant lié stocke un chemin d’accès aux données d’origine, souvent dans un fichier séparé.

Par exemple, si vous travaillez dans un document de traitement de texte et que vous créez un élément lié à certaines cellules d’une feuille de calcul, les données de l’élément lié sont stockées dans le document de feuille de calcul d’origine. Le document de traitement de texte contient uniquement les informations spécifiant l’emplacement où se trouve l’élément, c’est-à-dire qu’il contient un lien vers le document de feuille de calcul d’origine. Lorsque vous double-cliquez sur les cellules, l’application de feuille de calcul est lancée et le document de feuille de calcul d’origine est chargé à partir de l’emplacement où il a été stocké.

Chaque élément OLE, qu’il soit incorporé ou lié, est associé à un type en fonction de l’application qui l’a créé. Par exemple, un élément Microsoft Paintbrush est un type d’élément, et un élément Microsoft Excel est un autre type. Toutefois, certaines applications peuvent créer plusieurs types d’éléments. Par exemple, Microsoft Excel peut créer des éléments de feuille de calcul, des éléments de graphique et des éléments de feuille de calcul. Chacun de ces éléments peut être identifié de manière unique par le système à l’aide d’un identificateur de classe ou d’un **CLSID**.

## <a name="see-also"></a>Voir aussi

[Arrière-plan OLE](ole-background.md)<br/>
[Arrière-plan OLE : conteneurs et serveurs](ole-background-containers-and-servers.md)<br/>
[Conteneurs : éléments clients](containers-client-items.md)<br/>
[Serveurs : éléments du serveur](servers-server-items.md)
