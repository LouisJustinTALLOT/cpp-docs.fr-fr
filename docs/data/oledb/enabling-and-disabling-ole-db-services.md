---
title: Activation et désactivation des services OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: c5eaff8b3b37096eeca8777b6ba8bb91e01d7cd2
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265202"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Activation et désactivation des services OLE DB

Le Gestionnaire de composants de Service OLE DB compare les propriétés spécifiées par le consommateur pour les propriétés prises en charge par le fournisseur pour déterminer si les composants de services individuels peuvent être utilisés pour répondre à des fonctionnalités étendues demandées par le consommateur. Par exemple, si une application demande un curseur de défilement et le fournisseur prend en charge uniquement un curseur avant uniquement, le Gestionnaire de composants de Service utilise le composant de service de moteur de curseur Client pour fournir la fonctionnalité de défilement. Si l’application repose sur les fonctionnalités étendues prises en charge par défaut sur l’ensemble de lignes du fournisseur, et que l’application ne définit pas explicitement les propriétés à demander cette fonctionnalité, la fonctionnalité ne peut pas apparaître sur l’ensemble de lignes retourné par le Client Moteur de curseur. Pour être interopérable, applications doivent toujours définir des propriétés pour demander explicitement des fonctionnalités étendues si nécessaire.

Dans certains cas, il peut être nécessaire de désactiver des services OLE DB pour fonctionner avec des applications existantes qui font des hypothèses sur les caractéristiques d’un fournisseur. Services OLE DB offrent la possibilité de désactiver des services individuels, ou tous les services, selon une base connexion par connexion ou pour toutes les applications à l’aide d’un seul fournisseur.

## <a name="see-also"></a>Voir aussi

[Services et regroupement des ressources OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)