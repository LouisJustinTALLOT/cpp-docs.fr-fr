---
title: Copier les sources, propriétés de projet (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: d13bc7c129696e2b7251ccb23b68338956864321
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325589"
---
# <a name="copy-sources-project-properties-linux-c"></a>Copier les sources, propriétés de projet (Linux C++)

Les propriétés définies dans cette page de propriétés s’appliquent à tous les fichiers contenus dans le projet, à l’exception de ceux pour lesquels des propriétés de niveau fichier sont définies.

Propriété | Description
--- | ---
Sources à copier | Spécifie les sources devant être copiées sur le système distant. Tout changement apporté à cette liste peut entraîner un décalage ou des répercussions dans la structure des répertoires où sont copiés les fichiers sur le système distant.
Copier les sources | Spécifie si les sources doivent être copiées sur le système distant.
Sources supplémentaires à copier | Spécifie les sources supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.
