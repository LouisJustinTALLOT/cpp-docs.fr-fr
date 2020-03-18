---
title: IDBCreateCommandImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: 27ca1fd20e8f358d936789da695611d96a6e7aa1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446130"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl, classe

Fournit une implémentation de l’interface [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Objet de session dérivé de `IDBCreateCommandImpl`.

*CommandClass*<br/>
Votre classe de commande.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

|||
|-|-|
|[CreateCommand](#createcommand)|Crée une nouvelle commande.|

## <a name="remarks"></a>Notes

Interface facultative sur l’objet session pour obtenir une nouvelle commande.

## <a name="createcommand"></a>Idbcreatecommandimpl, :: CreateCommand

Crée une nouvelle commande et retourne l’interface demandée.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Paramètres

Consultez [IDBCreateCommand :: CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

Certains paramètres correspondent à *OLE DB paramètres de référence du programmeur* de différents noms, décrits dans `IDBCreateCommand::CreateCommand`:

|Paramètres du modèle de OLE DB|Paramètres *de référence du programmeur OLE DB*|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)