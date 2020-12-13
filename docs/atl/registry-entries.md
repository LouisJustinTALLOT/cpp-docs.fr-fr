---
description: 'En savoir plus sur : entrées de Registre'
title: Entrées de Registre (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
ms.openlocfilehash: c89c8f64a91c09f16333c3381a33d792332543d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138578"
---
# <a name="registry-entries"></a>Entrées de Registre

DCOM a introduit le concept d’ID d’application (appid), qui regroupent les options de configuration pour un ou plusieurs objets DCOM dans un emplacement centralisé dans le registre. Vous spécifiez une AppID en indiquant sa valeur dans la valeur nommée AppID sous le CLSID de l’objet.

Par défaut, un service généré par ATL utilise son CLSID comme GUID pour son AppID. Sous `HKEY_CLASSES_ROOT\AppID` , vous pouvez spécifier des entrées spécifiques à DCOM. Au départ, il existe deux entrées :

- `LocalService`, avec une valeur égale au nom du service. Si cette valeur existe, elle est utilisée à la place de la `LocalServer32` clé sous le CLSID.

- `ServiceParameters`, avec une valeur égale à `-Service` . Cette valeur spécifie les paramètres qui seront passés au service au démarrage. Notez que ces paramètres sont passés à la fonction du service `ServiceMain` , et non à `WinMain` .

Tout service DCOM doit également créer une autre clé sous `HKEY_CLASSES_ROOT\AppID` . Cette clé est égale au nom de l’EXE et agit comme une référence croisée, car elle contient une valeur AppID qui pointe vers les entrées AppID.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)
