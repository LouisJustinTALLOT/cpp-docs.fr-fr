---
title: Conversion des données non prises en charge par le fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e60f6cd4f7dca1ed3e176cabefc42f69946436a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409068"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Conversion des données non prises en charge par le fournisseur

Lorsque le consommateur demande un type de données qui n’est pas pris en charge par le fournisseur, le modèle de fournisseur OLE DB de code pour `IRowsetImpl::GetData` appelle Msdadc.dll pour convertir le type de données.

Si vous implémentez une interface comme `IRowsetChange` qui requiert une conversion de données, vous pouvez appeler Msdaenum.dll pour effectuer la conversion. Utilisez `GetData`, définie dans Atldb.h, par exemple.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)