---
title: Entrées de Registre (ATL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac8e202fc2fc3d58e2d57a9fbfa15264d9fd310e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359727"
---
# <a name="registry-entries"></a>Entrées de Registre
DCOM a introduit le concept d’ID d’Application (appid), lequel regroupe les options de configuration pour un ou plusieurs objets DCOM dans un emplacement centralisé dans le Registre. Vous spécifiez un AppID en indiquant sa valeur dans la valeur nommée AppID sous CLSID de l’objet.  
  
 Par défaut, un service généré par ATL utilise son CLSID comme GUID pour son AppID. Sous `HKEY_CLASSES_ROOT\AppID`, vous pouvez spécifier des entrées spécifiques à DCOM. Au départ, il existe deux entrées :  
  
-   `LocalService`, avec une valeur égale au nom du service. Si cette valeur existe, il est utilisé à la place de la `LocalServer32` clé sous le CLSID.  
  
-   `ServiceParameters`, avec une valeur égale à `-Service`. Cette valeur spécifie les paramètres qui seront transmis au service lorsqu’il est démarré. Notez que ces paramètres sont passés à du service `ServiceMain` fonction non `WinMain`.  
  
 Tout service DCOM doit également créer une autre clé sous `HKEY_CLASSES_ROOT\AppID`. Cette clé est égale au nom du fichier EXE et agit comme une référence croisée, car elle contient une valeur AppID qui pointe vers les entrées AppID.  
  
## <a name="see-also"></a>Voir aussi  
 [Services](../atl/atl-services.md)

