---
title: IWorkerThreadClient Interface
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 1fa8a5e42d002260076f737d3d33cfa191ff297a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197404"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient Interface

`IWorkerThreadClient` est l’interface implémentée par les clients de la [CWorkerThread](../../atl/reference/cworkerthread-class.md) classe.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CloseHandle](#closehandle)|Implémentez cette méthode pour fermer le handle associé à cet objet.|
|[Execute](#execute)|Implémentez cette méthode pour exécuter du code lorsque le handle associé à cet objet est signalé.|

## <a name="remarks"></a>Notes

Implémentez cette interface lorsque vous avez du code qui doit s’exécuter sur un thread de travail en réponse à un handle ne soit signalé.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Implémentez cette méthode pour fermer le handle associé à cet objet.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Paramètres

*hHandle*<br/>
Le handle à fermer.

### <a name="return-value"></a>Valeur de retour

Sur la réussite ou une erreur HRESULT en cas d’échec, retourne S_OK.

### <a name="remarks"></a>Notes

Le handle passé à cette méthode a été précédemment associé à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant montre une implémentation simple de `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Implémentez cette méthode pour exécuter du code lorsque le handle associé à cet objet est signalé.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Paramètres

*dwParam*<br/>
Le paramètre utilisateur.

*hObject*<br/>
Le handle qui a été signalé.

### <a name="return-value"></a>Valeur de retour

Sur la réussite ou une erreur HRESULT en cas d’échec, retourne S_OK.

### <a name="remarks"></a>Notes

Le handle et la valeur DWORD/pointeur passé à cette méthode ont été précédemment associé à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant montre une implémentation simple de `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread, classe](../../atl/reference/cworkerthread-class.md)
