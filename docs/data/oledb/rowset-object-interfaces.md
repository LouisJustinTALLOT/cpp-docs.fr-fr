---
title: Interfaces de l’objet d’ensemble de lignes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e8a1a5f5256087a8869426489fe01250b16fc598
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340509"
---
# <a name="rowset-object-interfaces"></a>Interfaces de l'objet rowset
Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet d’ensemble de lignes.  
  
|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](https://msdn.microsoft.com/library/ms719672.aspx)|Obligatoire|Oui|  
|[IColumnsInfo](https://msdn.microsoft.com/library/ms724541.aspx)|Obligatoire|Oui|  
|[IConvertType](https://msdn.microsoft.com/library/ms715926.aspx)|Obligatoire|Oui|  
|[IRowset](https://msdn.microsoft.com/library/ms720986.aspx)|Obligatoire|Oui|  
|[IRowsetInfo](https://msdn.microsoft.com/library/ms724541.aspx)|Obligatoire|Oui|  
|[IChapteredRowset](https://msdn.microsoft.com/library/ms718180.aspx)|Facultatif|Non|  
|[IColumnsInfo2](https://msdn.microsoft.com/library/ms712953.aspx)|Facultatif|Non|  
|[IColumnsRowset](https://msdn.microsoft.com/library/ms722657.aspx)|Facultatif|Non|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Facultatif|Oui (via ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/library/ms709832.aspx)|Facultatif|Non|  
|[IGetRow](https://msdn.microsoft.com/library/ms718047.aspx)|Facultatif|Non|  
|[IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx)|Facultatif|Oui|  
|[IRowsetChapterMember](https://msdn.microsoft.com/library/ms725430.aspx)|Facultatif|Non|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/library/ms709700.aspx)|Facultatif|Non|  
|[IRowsetFind](https://msdn.microsoft.com/library/ms724221.aspx)|Facultatif|Non|  
|[IRowsetIdentity](https://msdn.microsoft.com/library/ms715913.aspx)|Facultative (mais requise pour les fournisseurs de niveau 0)|Oui|  
|[IRowsetIndex](https://msdn.microsoft.com/library/ms719604.aspx)|Facultatif|Non|  
|[IRowsetLocate](https://msdn.microsoft.com/library/ms721190.aspx)|Facultatif|Oui|  
|[IRowsetRefresh](https://msdn.microsoft.com/library/ms714892.aspx)|Facultatif|Non|  
|[IRowsetScroll](https://msdn.microsoft.com/library/ms712984.aspx)|Facultatif|Non|  
|[IRowsetUpdate](https://msdn.microsoft.com/library/ms714401.aspx)|Facultatif|Oui|  
|[IRowsetView](https://msdn.microsoft.com/library/ms709755.aspx)|Facultatif|Non|  
|[ISupportErrorInfo](https://msdn.microsoft.com/library/ms715816.aspx)|Facultatif|Oui|  
|[IRowsetBookmark](https://msdn.microsoft.com/library/ms714246.aspx)|Facultatif|Non|  
  
 L’objet d’ensemble de lignes générées par l’Assistant implémente `IAccessor`, `IRowset`, et `IRowsetInfo` via l’héritage. Le `IAccessorImpl` lie les deux colonnes de sortie. Le `IRowset` interface contrôle les extractions de lignes et de données. Le `IRowsetInfo` interface gère les propriétés de l’ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)