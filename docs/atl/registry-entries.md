---
title: Entrées de Registre (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
ms.openlocfilehash: b61aae9ba9316dded1dcb11353e52eb2fffd49a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472876"
---
# <a name="registry-entries"></a>Entrées de Registre

DCOM a introduit le concept d’ID d’Application (appid), lequel regrouper les options de configuration pour un ou plusieurs objets DCOM dans un emplacement centralisé dans le Registre. Vous spécifiez un AppID en indiquant sa valeur dans la valeur nommée AppID sous CLSID de l’objet.

Par défaut, un service généré par ATL utilise son CLSID comme GUID pour son AppID. Sous `HKEY_CLASSES_ROOT\AppID`, vous pouvez spécifier des entrées spécifiques à DCOM. Initialement, il existe deux entrées :

- `LocalService`, avec une valeur égale au nom du service. Si cette valeur existe, elle est utilisée au lieu du `LocalServer32` clé sous le CLSID.

- `ServiceParameters`, avec une valeur égale à `-Service`. Cette valeur spécifie les paramètres qui seront transmis au service lorsqu’il est démarré. Notez que ces paramètres sont passés à du service `ServiceMain` fonction non `WinMain`.

N’importe quel service DCOM doit également créer une autre clé sous `HKEY_CLASSES_ROOT\AppID`. Cette clé est égale au nom du fichier EXE et agit comme une référence croisée, car elle contient une valeur AppID qui pointe vers les entrées AppID.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)

