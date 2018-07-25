---
title: CTable, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7dc1383199b5e8167936d99d487bdfc3eb15bddb
ms.sourcegitcommit: b217daee32d3413cf33753d9b4dc35a0022b1bfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233488"
---
# <a name="ctable-class"></a>CTable, classe
Fournit un moyen d’accéder directement à un rowset simple (sans paramètres).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor, 
            template <typename T> class TRowset = CRowset>  
class CTable :  
   public CAccessorRowset <TAccessor, TRowset>  
```  
  
### <a name="parameters"></a>Paramètres  
 *TAccessor*  
 Classe d’accesseur.  
  
 *TRowset*  
 Une classe rowset.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbcli.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[Ouvrir](#open)|La table s’ouvre.|  
  
## <a name="remarks"></a>Notes  
 Consultez [CCommand](../../data/oledb/ccommand-class.md) pour plus d’informations sur la façon d’exécuter une commande pour accéder à un ensemble de lignes.  

## <a name="open"></a> CTable::Open
La table s’ouvre.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *session*  
 [in] La session pour laquelle la table est ouvert.  
  
 *wszTableName*  
 [in] Le nom de la table à ouvrir, transmis sous forme de chaîne Unicode.  
  
 *szTableName*  
 [in] Le nom de la table à ouvrir, transmis sous forme de chaîne ANSI.  
  
 *dbid*  
 [in] Le `DBID` de la table à ouvrir.  
  
 *pPropSet*  
 [in] Un pointeur vers un tableau de [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](https://msdn.microsoft.com/library/ms713696.aspx) dans le *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows. La valeur par défaut NULL ne spécifie aucuns propriétés.  
  
 *ulPropSets*  
 [in] Le nombre de [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) structures passées dans le *pPropSet* argument.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) dans le *de référence du programmeur OLE DB*.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
