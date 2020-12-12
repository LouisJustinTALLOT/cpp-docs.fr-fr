---
description: En savoir plus sur l’activation et la désactivation de services pour un fournisseur
title: Activation et désactivation de services pour un fournisseur
ms.date: 07/30/2019
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: ead2ce9b8f1e678af00bcc03140c2868986a1564
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287539"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Activation et désactivation de services pour un fournisseur

Les services OLE DB individuels peuvent être activés ou désactivés par défaut pour toutes les applications qui accèdent à un seul fournisseur. Pour ce faire, ajoutez une entrée de Registre OLEDB_SERVICES sous le CLSID du fournisseur, avec une valeur DWORD spécifiant les services à activer ou désactiver, comme indiqué dans le tableau suivant.

|Services par défaut activés|Valeur DWORD|
|------------------------------|-------------------|
|Tous les services à l’exception du curseur client et du regroupement|0xfffffffa|
|Tous les services à l’exception du curseur client|0xfffffffb|
|Tous les services à l’exception du regroupement et de l’inscription automatique|0xfffffffc|
|Tous les services à l’exception du regroupement|0xfffffffe|
|Tous les services (par défaut)|égale|
|Aucun service|0x00000000|
|Aucune agrégation, tous les services sont désactivés|Aucune entrée de Registre OLEDB_Services|

## <a name="see-also"></a>Voir aussi

[Activation et désactivation de services OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)
