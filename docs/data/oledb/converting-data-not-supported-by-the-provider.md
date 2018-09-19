---
title: Conversion de données non pris en charge par le fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa9fed1f7c779efc7104ec8138d618b85aeb2a33
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081739"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Conversion des données non prises en charge par le fournisseur

Lorsque le consommateur demande un type de données qui n’est pas pris en charge par le fournisseur, le modèle de fournisseur OLE DB de code pour `IRowsetImpl::GetData` appelle Msdadc.dll pour convertir le type de données.  
  
Si vous implémentez une interface comme `IRowsetChange` qui requiert une conversion de données, vous pouvez appeler Msdaenum.dll pour effectuer la conversion. Utilisez `GetData`, définie dans Atldb.h, par exemple.  
  
## <a name="see-also"></a>Voir aussi  

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)