---
title: Icolumnsinfoimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- GetColumnInfo
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
dev_langs:
- C++
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bde6a3947d7afa836d93387e80c9b7885b1bc15c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099406"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl, classe

Fournit une implémentation de la [IColumnsInfo](/previous-versions/windows/desktop/ms724541\(v=vs.85\)) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>  
class ATL_NO_VTABLE IColumnsInfoImpl :   
   public IColumnsInfo,    
   public CDBIDOps  
```  
  
### <a name="parameters"></a>Paramètres  

*T*<br/>
Votre classe, dérivée de `IColumnsInfoImpl`.  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[GetColumnInfo](#getcolumninfo)|Retourne les métadonnées de colonne requises par la plupart des consommateurs.|  
|[MapColumnIDs](#mapcolumnids)|Retourne un tableau d’ordinaux des colonnes dans un ensemble de lignes qui sont identifiés par l’ID de colonne spécifié.|  
  
## <a name="remarks"></a>Notes  

Une interface obligatoire sur les ensembles de lignes et de commandes. Pour modifier le comportement de votre fournisseur de `IColumnsInfo` implémentation, vous devez modifier le mappage de colonnes du fournisseur.  

## <a name="getcolumninfo"></a> IColumnsInfoImpl::GetColumnInfo

Retourne les métadonnées de colonne requises par la plupart des consommateurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,  
   DBCOLUMNINFO** prgInfo,  
   OLECHAR** ppStringsBuffer);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  

## <a name="mapcolumnids"></a> IColumnsInfoImpl::MapColumnIDs

Retourne un tableau d’ordinaux des colonnes dans un ensemble de lignes qui sont identifiés par l’ID de colonne spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,  
   const DBID rgColumnIDs[],  
   DBORDINAL rgColumns[]);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IColumnsInfo::MapColumnIDs](/previous-versions/windows/desktop/ms714200\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
## <a name="see-also"></a>Voir aussi  

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)