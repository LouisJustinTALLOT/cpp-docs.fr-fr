---
title: Modification de l’héritage de RMyProviderRowset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 407406683f03dbba2d582b1ae24d5cc3bb8680a5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336463"
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>Modification de l'héritage de RMyProviderRowset
Pour ajouter le `IRowsetLocate` l’interface à l’exemple de fournisseur simple en lecture seule, modifiez l’héritage de `RMyProviderRowset`. Initialement, `RMyProviderRowset` hérite `CRowsetImpl`. Vous devez modifier qu’elle hérite de `CRowsetBaseImpl`.  
  
 Pour ce faire, créez une nouvelle classe, `CMyRowsetImpl`, dans MyProviderRS.h :  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>  
{  
...  
};  
```  
  
 À présent, modifiez le mappage d’interface COM dans MyProviderRS.h comme suit :  
  
```cpp  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 Cette opération crée un mappage d’interface COM qui indique à `CMyRowsetImpl` pour appeler `QueryInterface` à la fois pour le `IRowset` et `IRowsetLocate` interfaces. Pour obtenir l’ensemble de l’implémentation pour l’ensemble de lignes autres classes, les liens de mappage les `CMyRowsetImpl` classe revenir à la `CRowsetBaseImpl` classe définis par les modèles OLE DB ; le mappage utilise la macro COM_INTERFACE_ENTRY_CHAIN, qui indique aux modèles OLE DB d’analyser le mappage COM dans `CRowsetBaseImpl` en réponse à une `QueryInterface` appeler.  
  
 Enfin, liez `RAgentRowset` à `CMyRowsetBaseImpl` en modifiant `RAgentRowset` d’hériter de `CMyRowsetImpl`, comme suit :  
  
```cpp  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset` peuvent désormais utiliser le `IRowsetLocate` interface tout en tirant parti du reste de l’implémentation pour la classe rowset.  
  
 Dans ce cas, vous pouvez [déterminer dynamiquement les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Amélioration du fournisseur simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md)