---
title: Conversion des données non prises en charge par le fournisseur
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: a53781f71a55dfb07dc996e5e25644d9337e4c63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473436"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Conversion des données non prises en charge par le fournisseur

Lorsque le consommateur demande un type de données qui n’est pas pris en charge par le fournisseur, le modèle de fournisseur OLE DB de code pour `IRowsetImpl::GetData` appelle Msdadc.dll pour convertir le type de données.

Si vous implémentez une interface comme `IRowsetChange` qui requiert une conversion de données, vous pouvez appeler Msdaenum.dll pour effectuer la conversion. Utilisez `GetData`, définie dans Atldb.h, par exemple.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)