---
title: ICommandImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: c5e599b437f7660801a1eb40618eb49bee84a918
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556814"
---
# <a name="icommandimpl-class"></a>ICommandImpl, classe

Fournit l’implémentation pour le [ICommand](https://docs.microsoft.com/previous-versions/windows/desktop/ms709737(v=vs.85)) interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `ICommandImpl`.

*CommandBase*<br/>
Une interface de commande. La valeur par défaut est `ICommand`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Annuler](#cancel)|Annule l’exécution de la commande actuelle.|
|[CancelExecution](#cancelexecution)|Annule l’exécution de la commande actuelle.|
|[CreateRowset](#createrowset)|Crée un objet d’ensemble de lignes.|
|[Execute](#execute)|Exécute la commande.|
|[GetDBSession](#getdbsession)|Retourne un pointeur d’interface à la session qui a créé la commande.|
|[ICommandImpl](#icommandimpl)|Constructeur.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_bCancel](#bcancel)|Indique si la commande doit être annulée.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Indique si la commande doit être annulée lors de l’exécution.|
|[m_bIsExecuting](#bisexecuting)|Indique si la commande est en cours d’exécution.|

## <a name="remarks"></a>Notes

Une interface obligatoire sur l’objet command.

## <a name="cancel"></a> ICommandImpl::Cancel

Annule l’exécution de la commande actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Notes

Consultez [ICommand::Cancel](https://docs.microsoft.com/previous-versions/windows/desktop/ms714402(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="cancelexecution"></a> ICommandImpl::CancelExecution

Annule l’exécution de la commande actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CancelExecution();
```

## <a name="createrowset"></a> ICommandImpl::CreateRowset

Appelé par [Execute](../../data/oledb/icommandimpl-execute.md) pour créer un ensemble de lignes unique.

### <a name="syntax"></a>Syntaxe

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Paramètres

*RowsetClass*<br/>
Un membre de classe de modèle représentant la classe d’ensemble de lignes de l’utilisateur. Généralement, généré par l’Assistant.

*pUnkOuter*<br/>
[in] Un pointeur vers le contrôle `IUnknown` si l’ensemble de lignes est créé dans le cadre d’un agrégat de l’interface ; sinon, elle a la valeur null.

*riid*<br/>
[in] Correspond à *riid* dans `ICommand::Execute`.

*pParams*<br/>
[entrée/sortie] Correspond à *pParams* dans `ICommand::Execute`.

*pcRowsAffected*<br/>
Correspond à *pcRowsAffected* dans `ICommand::Execute`.

*ppRowset*<br/>
[entrée/sortie] Correspond à *ppRowset* dans `ICommand::Execute`.

*pRowsetObj*<br/>
[out] Pointeur vers un objet d’ensemble de lignes. En général, ce paramètre n’est pas utilisé, mais il peut être utilisé si vous devez effectuer plus de travail sur l’ensemble de lignes avant de le transmettre à un objet COM. La durée de vie de *pRowsetObj* est liée par *ppRowset*.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard. Consultez `ICommand::Execute` pour obtenir la liste de valeurs standard.

### <a name="remarks"></a>Notes

Pour créer plus d’un ensemble de lignes, ou pour fournir vos propres conditions pour la création de différents ensembles de lignes, placez les différents appels à `CreateRowset` depuis `Execute`.

Consultez [ICommand::Execute](https://docs.microsoft.com/previous-versions/windows/desktop/ms718095(v=vs.85)) dans le *de référence du programmeur OLE DB.*

## <a name="execute"></a> ICommandImpl::Execute

Exécute la commande.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommand::Execute](https://docs.microsoft.com/previous-versions/windows/desktop/ms718095(v=vs.85)) dans le *de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

L’interface sortante demandé sera une interface acquise à partir de l’objet d’ensemble de lignes qui crée cette fonction.

`Execute` appels [CreateRowset](../../data/oledb/icommandimpl-createrowset.md). Substituer l’implémentation par défaut pour créer plus d’un ensemble de lignes ou pour fournir vos propres conditions pour la création de différents ensembles de lignes.

## <a name="getdbsession"></a> ICommandImpl::GetDBSession

Retourne un pointeur d’interface à la session qui a créé la commande.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommand::GetDBSession](https://docs.microsoft.com/previous-versions/windows/desktop/ms719622(v=vs.85)) dans le *de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Utile pour récupérer des propriétés de la session.

## <a name="icommandimpl"></a> ICommandImpl::ICommandImpl

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
ICommandImpl();
```

## <a name="bcancel"></a> ICommandImpl::m_bCancel

Indique si la commande est annulée.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Notes

Vous pouvez récupérer cette variable dans le `Execute` méthode de votre classe de commande, puis annuler comme il convient.

## <a name="bcancelwhenexecuting"></a> ICommandImpl::m_bCancelWhenExecuting

Indique si la commande peut être annulée lors de l’exécution.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Notes

Valeur par défaut est **true** (peut être annulée).

## <a name="bisexecuting"></a> ICommandImpl::m_bIsExecuting

Indique si la commande est en cours d’exécution.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Notes

Le `Execute` méthode de votre classe de commande peut définir cette variable sur **true**.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)