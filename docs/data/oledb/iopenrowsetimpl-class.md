---
title: Iopenrowsetimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84050dcf4faed8bb99b871d3b797400c1ed5620e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086952"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl, classe

Fournit l’implémentation pour le `IOpenRowset` interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
### <a name="parameters"></a>Paramètres  

*SessionClass*<br/>
Votre classe, dérivée de `IOpenRowsetImpl`.  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CreateRowset](#createrowset)|Crée un objet d’ensemble de lignes. Pas appelée directement par l’utilisateur.|  
|[OpenRowset](#openrowset)|Ouvre et retourne un ensemble de lignes qui inclut toutes les lignes à partir d’une seule table de base ou un index. (Pas dans ATLDB. H)|  
  
## <a name="remarks"></a>Notes  

Le [IOpenRowset](/previous-versions/windows/desktop/ms716946\(v=vs.85\)) interface est obligatoire pour un objet de session. Il s’ouvre et retourne un ensemble de lignes qui inclut toutes les lignes à partir d’une seule table de base ou un index.  
  
## <a name="createrowset"></a> IOpenRowsetImpl::CreateRowset

Crée un objet d’ensemble de lignes. Pas appelée directement par l’utilisateur. Consultez [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724\(v=vs.85\)) dans le *de référence du programmeur OLE DB.*  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
template template <class RowsetClass>  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Paramètres  

*RowsetClass*<br/>
Un membre de classe de modèle représentant la classe d’ensemble de lignes de l’utilisateur. Généralement, généré par l’Assistant.  
  
*pRowsetObj*<br/>
[out] Pointeur vers un objet d’ensemble de lignes. En général, ce paramètre n’est pas utilisé, mais il peut être utilisé si vous devez effectuer plus de travail sur l’ensemble de lignes avant de le transmettre à un objet COM. La durée de vie de *pRowsetObj* est liée par *ppRowset*.  
  
Pour les autres paramètres, consultez [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724\(v=vs.85\)) dans le *de référence du programmeur OLE DB.*  

## <a name="openrowset"></a> IOpenRowsetImpl::OpenRowset

Ouvre et retourne un ensemble de lignes qui inclut toutes les lignes à partir d’une seule table de base ou un index.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  

Cette méthode est introuvable dans ATLDB. H. Lorsque vous créez un fournisseur, il est créé par l’Assistant objet ATL.  
  
## <a name="see-also"></a>Voir aussi  

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)