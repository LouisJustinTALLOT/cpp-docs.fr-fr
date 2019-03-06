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
ms.openlocfilehash: 36f5a359051dbd5035a73514f84fb2c61ff13176
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412924"
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

## <a name="requirements"></a>Spécifications

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

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)