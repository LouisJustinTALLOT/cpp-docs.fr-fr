---
title: IRowsetChangeImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- SetData
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f77f9a33b0cf51ea54d16f89e86ea914640f627
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339596"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl Class
L’implémentation de modèles OLE DB de la [IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx) interface dans la spécification OLE DB.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Une classe dérivée de `IRowsetChangeImpl`.  
  
 *Stockage*  
 L’enregistrement utilisateur.  
  
 *BaseInterface*  
 La classe de base pour l’interface, tel que `IRowsetChange`.  
  
 *RowClass*  
 L’unité de stockage pour le handle de ligne.  
  
 *MapClass*  
 L’unité de stockage pour tous les handles de ligne détenus par le fournisseur.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisés avec IRowsetChange)  
  
|||  
|-|-|  
|[DeleteRows](#deleterows)|Supprime des lignes de l’ensemble de lignes.|  
|[InsertRow](#insertrow)|Insère une ligne dans l’ensemble de lignes.|  
|[SetData](#setdata)|Définit les valeurs de données dans une ou plusieurs colonnes.|  
  
### <a name="implementation-method-callback"></a>Méthode d’implémentation (rappel)  
  
|||  
|-|-|  
|[FlushData](#flushdata)|Substitué par le fournisseur pour valider des données dans son magasin.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est responsable des opérations d’écriture immédiate à une banque de données. « Immédiats » signifie que lorsque l’utilisateur final (la personne à l’aide du consommateur) effectue toutes les modifications, ces modifications sont immédiatement transmises aux données stocker (et ne peut pas être annulée).  
  
 `IRowsetChangeImpl` implémente la norme OLE DB `IRowsetChange` interface, ce qui permet la mise à jour des valeurs des colonnes dans les lignes existantes, la suppression de lignes et l’insertion de nouvelles lignes.  
  
 L’implémentation de modèles OLE DB prend en charge toutes les méthodes de base (`SetData`, `InsertRow`, et `DeleteRows`).  
  
> [!IMPORTANT]
>  Il est fortement recommandé que vous lire la documentation suivante avant de tenter d’implémenter votre fournisseur :  
  
-   [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Chapitre 6 de la *de référence du programmeur OLE DB*  
  
-   Consultez également comment la `RUpdateRowset` classe est utilisée dans l’exemple UpdatePV  
  
## <a name="deleterows"></a> IRowsetChangeImpl::DeleteRows
Supprime des lignes de l’ensemble de lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWSTATUS rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetChange::DeleteRows](https://msdn.microsoft.com/library/ms724362.aspx) dans le *de référence du programmeur OLE DB*. 

## <a name="insertrow"></a> IRowsetChangeImpl::InsertRow
Crée et initialise une nouvelle ligne dans l’ensemble de lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,  
   HACCESSOR hAccessor,  
   void* pData,  
   HROW* phRow);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetChange::InsertRow](https://msdn.microsoft.com/library/ms716921.aspx) dans le *de référence du programmeur OLE DB*. 

## <a name="setdata"></a> IRowsetChangeImpl::SetData
Définit les valeurs de données dans une ou plusieurs colonnes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetChange::SetData](https://msdn.microsoft.com/library/ms721232.aspx) dans le *de référence du programmeur OLE DB*. 

## <a name="flushdata"></a> IRowsetChangeImpl::FlushData
Substitué par le fournisseur pour valider des données dans son magasin.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT FlushData(HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *hRowToFlush*  
 [in] Handle vers les lignes pour les données. Le type de cette ligne est déterminé à partir de la *RowClass* argument template de la `IRowsetImpl` classe (`CSimpleRow` par défaut).  
  
 *hAccessorToFlush*  
 [in] Handle de l’accesseur qui contient les informations de liaison et les informations de type dans ses `PROVIDER_MAP` (consultez [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)