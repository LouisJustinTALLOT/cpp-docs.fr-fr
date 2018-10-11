---
title: CAccessorRowset, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- FreeRecordMemory
- GetColumnInfo
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ef9799c65f4932bf314f3c11fd8324e0fb40bf2
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081734"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset, classe

Encapsule un ensemble de lignes et de ses accesseurs associés dans une classe unique.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor, 
   template <typename T> class TRowset = CRowset>  
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>  
```  
  
### <a name="parameters"></a>Paramètres  

*TAccessor*<br/>
Classe d’accesseur.  
  
*TRowset*<br/>
Une classe rowset.  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldbcli.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[Bind](#bind)|Crée des liaisons (utilisée lorsque `bBind` est spécifié en tant que **false** dans [CCommand::Open](../../data/oledb/ccommand-open.md)).|  
|[CAccessorRowset](#caccessorrowset)|Constructeur.|  
|[Fermer](#close)|Ferme l’ensemble de lignes et de tous les accesseurs.|  
|[FreeRecordMemory](#freerecordmemory)|Libère toutes les colonnes dans l’enregistrement actif qui doivent être libérées.|  
|[GetColumnInfo](#getcolumninfo)|Implémente [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704).|  
  
## <a name="remarks"></a>Notes  

Classe `TAccessor` gère l’accesseur. Classe *TRowset* gère l’ensemble de lignes.  

## <a name="bind"></a> CAccessorRowset::Bind

Crée les liaisons, si vous avez spécifié `bBind` comme **false** dans [CCommand::Open](../../data/oledb/ccommand-open.md).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Bind();  
```  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  

## <a name="caccessorrowset"></a> CAccessorRowset::CAccessorRowset

Initialise le `CAccessorRowset` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CAccessorRowset();  
```  

## <a name="close"></a> CAccessorRowset::Close

Libère tous les accesseurs actives et l’ensemble de lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void Close();  
```  
  
### <a name="remarks"></a>Notes  

Libère la mémoire associée.  

## <a name="freerecordmemory"></a> CAccessorRowset::FreeRecordMemory

Libère toutes les colonnes dans l’enregistrement actif qui doivent être libérées.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void FreeRecordMemory();  
```  

## <a name="getcolumninfo"></a> CAccessorRowset::GetColumnInfo

Obtient des informations sur les colonnes à partir de l’ensemble de lignes ouvert.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns, 
   DBCOLUMNINFO** ppColumnInfo, 
   LPOLESTR* ppStrings) const; 
    
HRESULT GetColumnInfo(DBORDINAL* pColumns, 
   DBCOLUMNINFO** ppColumnInfo);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) dans le *de référence du programmeur OLE DB*.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

L’utilisateur doit libérer les informations de la colonne retournée et de la mémoire tampon de chaîne. Utilisez la deuxième version de cette méthode lorsque vous utilisez [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) et avez besoin de remplacer les liaisons.  
  
Pour plus d’informations, consultez [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) dans le *de référence du programmeur OLE DB*.  
  
## <a name="see-also"></a>Voir aussi  

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)