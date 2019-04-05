---
title: IDBCreateSessionImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
ms.openlocfilehash: ae59abc542a4599d289c099801fc34d56b2b13d4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028533"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl, classe

Fournit une implémentation pour le [IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85)) interface.

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

Consultez [IDBCreateSession::CreateSession](/previous-versions/windows/desktop/ms714942(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)