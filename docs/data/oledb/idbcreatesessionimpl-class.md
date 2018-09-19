---
title: Idbcreatesessionimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7f148176b8d5d0c85f3e899cfd117bbb381794b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047393"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl, classe

Fournit une implémentation pour le [IDBCreateSession](/previous-versions/windows/desktop/ms724076\(v=vs.85\)) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
### <a name="parameters"></a>Paramètres  

*T*<br/>
VOTRE CLASSE DÉRIVÉE  
  
*SessionClass*<br/>
L’objet de session.  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldb.h 
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[CreateSession](#createsession)|Crée une nouvelle session de l’objet de source de données et retourne l’interface demandée sur la session nouvellement créée.|  
  
## <a name="remarks"></a>Notes  

Une interface obligatoire sur les objets de source de données.  

## <a name="createsession"></a> IDBCreateSessionImpl::CreateSession

Crée une nouvelle session de l’objet de source de données et retourne l’interface demandée sur la session nouvellement créée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [IDBCreateSession::CreateSession](/previous-versions/windows/desktop/ms714942\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.   
  
## <a name="see-also"></a>Voir aussi  

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)