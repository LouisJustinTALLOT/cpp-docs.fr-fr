---
description: 'En savoir plus sur : classe Icolumnsinfoimpl,'
title: IColumnsInfoImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
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
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: 9f6586f4d0315904ea16baf5aa1837bc43107602
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317621"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl, classe

Fournit une implémentation de l’interface [IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo,
   public CDBIDOps
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IColumnsInfoImpl` .

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[GetColumnInfo](#getcolumninfo)|Retourne les métadonnées de colonne exigées par la plupart des consommateurs.|
|[MapColumnIDs](#mapcolumnids)|Retourne un tableau des numéros des colonnes dans un jeu de lignes identifiées par les ID de colonne spécifiés.|

## <a name="remarks"></a>Notes

Interface obligatoire sur les ensembles de lignes et les commandes. Pour modifier le comportement de l’implémentation de votre fournisseur `IColumnsInfo` , vous devez modifier le mappage de colonnes du fournisseur.

## <a name="icolumnsinfoimplgetcolumninfo"></a><a name="getcolumninfo"></a> Icolumnsinfoimpl, :: GetColumnInfo

Retourne les métadonnées de colonne exigées par la plupart des consommateurs.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>Paramètres

Consultez [IColumnsInfo :: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="icolumnsinfoimplmapcolumnids"></a><a name="mapcolumnids"></a> Icolumnsinfoimpl, :: MapColumnIDs

Retourne un tableau des numéros des colonnes dans un jeu de lignes identifiées par les ID de colonne spécifiés.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [IColumnsInfo :: MapColumnIDs](/previous-versions/windows/desktop/ms714200(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
