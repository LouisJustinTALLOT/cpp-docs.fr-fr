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
ms.openlocfilehash: c88554d717888719ad6d805a2871489ce4b0df32
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845586"
---
# <a name="icommandimpl-class"></a>ICommandImpl, classe

Fournit l’implémentation pour l’interface [ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `ICommandImpl` .

*CommandBase*<br/>
Interface de commande. La valeur par défaut est `ICommand`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[Annuler](#cancel)|Annule l’exécution de la commande actuelle.|
|[CancelExecution](#cancelexecution)|Annule l’exécution de la commande actuelle.|
|[CreateRowset](#createrowset)|Crée un objet d’ensemble de lignes.|
|[Execute](#execute)|Exécute la commande.|
|[GetDBSession](#getdbsession)|Retourne un pointeur d’interface vers la session qui a créé la commande.|
|[ICommandImpl](#icommandimpl)|Constructeur.|

### <a name="data-members"></a>Données membres

| Nom | Description |
|-|-|
|[m_bCancel](#bcancel)|Indique si la commande doit être annulée.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Indique si la commande doit être annulée lors de l’exécution de.|
|[m_bIsExecuting](#bisexecuting)|Indique si la commande est en cours d’exécution.|

## <a name="remarks"></a>Notes

Interface obligatoire sur l’objet de commande.

## <a name="icommandimplcancel"></a><a name="cancel"></a> ICommandImpl :: Cancel

Annule l’exécution de la commande actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Notes

Consultez [ICommand :: Cancel](/previous-versions/windows/desktop/ms714402(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="icommandimplcancelexecution"></a><a name="cancelexecution"></a> ICommandImpl :: CancelExecution

Annule l’exécution de la commande actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CancelExecution();
```

## <a name="icommandimplcreaterowset"></a><a name="createrowset"></a> ICommandImpl :: CreateRowset

Appelée par [Execute](../../data/oledb/icommandimpl-execute.md) pour créer un ensemble de lignes unique.

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
Membre de classe de modèle qui représente la classe d’ensemble de lignes de l’utilisateur. Généralement généré par l’Assistant.

*pUnkOuter*<br/>
dans Pointeur vers l’interface de contrôle `IUnknown` si l’ensemble de lignes est créé dans le cadre d’un agrégat ; sinon, il a la valeur null.

*riid*<br/>
dans Correspond à *riid* dans `ICommand::Execute` .

*pParams*<br/>
[in/out] Correspond à *pParams* dans `ICommand::Execute` .

*pcRowsAffected*<br/>
Correspond à *pcRowsAffected* dans `ICommand::Execute` .

*ppRowset*<br/>
[in/out] Correspond à *ppRowset* dans `ICommand::Execute` .

*pRowsetObj*<br/>
à Pointeur vers un objet d’ensemble de lignes. En général, ce paramètre n’est pas utilisé, mais il peut être utilisé si vous devez effectuer davantage de travail sur l’ensemble de lignes avant de le passer à un objet COM. La durée de vie de *pRowsetObj* est liée par *ppRowset*.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard. `ICommand::Execute`Pour obtenir la liste des valeurs standard, consultez.

### <a name="remarks"></a>Notes

Pour créer plusieurs ensembles de lignes, ou pour fournir vos propres conditions de création de jeux de lignes différents, placez les différents appels à `CreateRowset` à partir de `Execute` .

Consultez [ICommand :: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) dans le *Guide de référence du programmeur OLE DB.*

## <a name="icommandimplexecute"></a><a name="execute"></a> ICommandImpl :: Execute

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

Consultez [ICommand :: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

L’interface sortante demandée sera une interface acquise à partir de l’objet rowset créé par cette fonction.

`Execute` appelle [CreateRowset](../../data/oledb/icommandimpl-createrowset.md). Remplacez l’implémentation par défaut pour créer plusieurs ensembles de lignes ou pour fournir vos propres conditions pour la création de différents ensembles de lignes.

## <a name="icommandimplgetdbsession"></a><a name="getdbsession"></a> ICommandImpl :: GetDBSession

Retourne un pointeur d’interface vers la session qui a créé la commande.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommand :: GetDBSession](/previous-versions/windows/desktop/ms719622(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Utile pour la récupération des propriétés de la session.

## <a name="icommandimplicommandimpl"></a><a name="icommandimpl"></a> ICommandImpl :: ICommandImpl

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
ICommandImpl();
```

## <a name="icommandimplm_bcancel"></a><a name="bcancel"></a> ICommandImpl :: m_bCancel

Indique si la commande est annulée.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Notes

Vous pouvez récupérer cette variable dans la `Execute` méthode de votre classe Command et l’annuler, le cas échéant.

## <a name="icommandimplm_bcancelwhenexecuting"></a><a name="bcancelwhenexecuting"></a> ICommandImpl :: m_bCancelWhenExecuting

Indique si la commande peut être annulée lors de l’exécution de.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Notes

La valeur par défaut **`true`** est (peut être annulée).

## <a name="icommandimplm_bisexecuting"></a><a name="bisexecuting"></a> ICommandImpl :: m_bIsExecuting

Indique si la commande est en cours d’exécution.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Notes

La `Execute` méthode de votre classe Command peut affecter la valeur à cette variable **`true`** .

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
