---
title: IDBCreateCommandImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: fda12332ef14cb95e9f11f8df0b94ccfffa0303d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425183"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl, classe

Fournit une implémentation de la [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Dérivé de l’objet de session `IDBCreateCommandImpl`.

*CommandClass*<br/>
Votre classe de commande.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d’interface

|||
|-|-|
|[CreateCommand](#createcommand)|Crée une nouvelle commande.|

## <a name="remarks"></a>Notes

Une interface facultative sur l’objet de session pour obtenir une nouvelle commande.

## <a name="createcommand"></a> IDBCreateCommandImpl::CreateCommand

Crée une nouvelle commande et retourne l’interface demandée.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Paramètres

Consultez [IDBCreateCommand::CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) dans le *de référence du programmeur OLE DB*.

Certains paramètres correspondent aux *de référence du programmeur OLE DB* des noms différents, qui sont décrites dans les paramètres `IDBCreateCommand::CreateCommand`:

|Paramètres de modèle OLE DB|*Référence du programmeur OLE DB* paramètres|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)