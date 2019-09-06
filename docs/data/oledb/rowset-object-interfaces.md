---
title: Interfaces de l'objet rowset
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: d9c2c61714a98d9de09d8657352a14f296e35a58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311661"
---
# <a name="rowset-object-interfaces"></a>Interfaces de l'objet rowset

Le tableau suivant indique les interfaces obligatoires et facultatives définies par OLE DB pour un objet d’ensemble de lignes.

|Interface|Requis ?|Implémenté par OLE DB modèles ?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|Obligatoire|Oui|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Obligatoire|Oui|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|Obligatoire|Oui|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|Obligatoire|Oui|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Obligatoire|Oui|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|Facultatif|Non|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|Facultatif|Non|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|Facultatif|Non|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Facultatif|Oui (via ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|Facultatif|Non|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|Facultatif|Non|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|Facultatif|Oui|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|Facultatif|Non|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|Facultatif|Non|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|Facultatif|Non|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|Facultatif (mais requis pour les fournisseurs de niveau 0)|Oui|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|Facultatif|Non|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|Facultatif|Oui|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|Facultatif|Non|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|Facultatif|Non|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|Facultatif|Oui|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|Facultatif|Non|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Facultatif|Oui|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|Facultatif|Non|

L’objet d’ensemble de lignes généré par `IAccessor`l' `IRowset`Assistant implémente, et `IRowsetInfo` via l’héritage. Le `IAccessorImpl` lie les deux colonnes de sortie. L' `IRowset` interface gère les extractions de lignes et de données. L' `IRowsetInfo` interface gère les propriétés de l’ensemble de lignes.

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
