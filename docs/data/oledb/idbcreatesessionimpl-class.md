---
description: 'En savoir plus sur : classe Idbcreatesessionimpl,'
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
ms.openlocfilehash: 8456ce4ec7bde5721ac6753ed9ec64d69c63e41f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317478"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl, classe

Fournit une implémentation pour l’interface [méthode IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>Paramètres

*T*<br/>
VOTRE CLASSE, DÉRIVÉE DE

*SessionClass*<br/>
Objet de session.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[CreateSession](#createsession)|Crée une nouvelle session à partir de l’objet source de données et retourne l’interface demandée sur la session nouvellement créée.|

## <a name="remarks"></a>Notes

Interface obligatoire sur les objets de source de données.

## <a name="idbcreatesessionimplcreatesession"></a><a name="createsession"></a> Idbcreatesessionimpl, :: CreateSession

Crée une nouvelle session à partir de l’objet source de données et retourne l’interface demandée sur la session nouvellement créée.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>Paramètres

Consultez [méthode IDBCreateSession :: CreateSession](/previous-versions/windows/desktop/ms714942(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
