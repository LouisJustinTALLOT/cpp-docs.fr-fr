---
description: 'En savoir plus sur : conversion de données non prises en charge par le fournisseur'
title: Conversion des données non prises en charge par le fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: 9fb449247ff40118e89dbebee5f43a1208a1f181
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323364"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Conversion des données non prises en charge par le fournisseur

Lorsque le consommateur demande un type de données qui n’est pas pris en charge par le fournisseur, le OLE DB code du modèle de fournisseur pour les `IRowsetImpl::GetData` appels Msdadc.dll pour convertir le type de données.

Si vous implémentez une interface telle `IRowsetChange` que nécessitant une conversion de données, vous pouvez appeler Msdaenum.dll pour effectuer la conversion. Utilisez `GetData` , défini dans Atldb. h, à titre d’exemple.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
