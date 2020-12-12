---
description: En savoir plus sur l’activation et la désactivation de services OLE DB
title: Activation et désactivation des services OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: a2a3e51b69a0051b6a231d14c18f3b1f416fb547
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317660"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Activation et désactivation des services OLE DB

Le gestionnaire de composants de service OLE DB compare les propriétés spécifiées par le consommateur aux propriétés prises en charge par le fournisseur pour déterminer si des composants de service individuels peuvent être utilisés pour répondre aux fonctionnalités étendues demandées par le consommateur. Par exemple, si une application demande un curseur à défilement et que le fournisseur ne prend en charge qu’un curseur avant uniquement, le gestionnaire de composants de service utilise le composant de service de moteur de curseur client pour fournir des fonctionnalités de défilement. Si l’application s’appuie sur des fonctionnalités étendues prises en charge par défaut dans l’ensemble de lignes du fournisseur et que l’application ne définit pas explicitement les propriétés pour demander cette fonctionnalité, les fonctionnalités peuvent ne pas apparaître sur l’ensemble de lignes retourné par le moteur de curseur client. Pour être interopérable, les applications doivent toujours définir des propriétés pour demander explicitement des fonctionnalités étendues si nécessaire.

Dans certains cas, il peut être nécessaire de désactiver les services OLE DB individuels pour fonctionner correctement avec les applications existantes qui font des hypothèses sur les caractéristiques d’un fournisseur. Les services de OLE DB permettent de désactiver des services individuels, ou tous les services, soit connexion par connexion, soit pour toutes les applications à l’aide d’un fournisseur unique.

## <a name="see-also"></a>Voir aussi

[OLE DB de la mise en pool des ressources et des services](../../data/oledb/ole-db-resource-pooling-and-services.md)
