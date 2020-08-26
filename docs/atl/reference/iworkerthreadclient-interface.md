---
title: Interface IWorkerThreadClient
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: aa72f090a006d6936339582a919b0faf5cab6b03
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835348"
---
# <a name="iworkerthreadclient-interface"></a>Interface IWorkerThreadClient

`IWorkerThreadClient` est l’interface implémentée par les clients de la classe [CWorkerThread](../../atl/reference/cworkerthread-class.md) .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[CloseHandle](#closehandle)|Implémentez cette méthode pour fermer le handle associé à cet objet.|
|[Execute](#execute)|Implémentez cette méthode pour exécuter du code lorsque le handle associé à cet objet est signalé.|

## <a name="remarks"></a>Notes

Implémentez cette interface lorsque vous avez du code qui doit s’exécuter sur un thread de travail en réponse à un handle qui devient signalé.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil. h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a> IWorkerThreadClient :: CloseHandle

Implémentez cette méthode pour fermer le handle associé à cet objet.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Paramètres

*hHandle*<br/>
Handle à fermer.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Le handle passé à cette méthode a été précédemment associé à cet objet par un appel à [CWorkerThread :: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant illustre une implémentation simple de `IWorkerThreadClient::CloseHandle` .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a> IWorkerThreadClient :: Execute

Implémentez cette méthode pour exécuter du code lorsque le handle associé à cet objet est signalé.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Paramètres

*dwParam*<br/>
Paramètre utilisateur.

*hObject*<br/>
Handle qui a été signalé.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Le handle et le DWORD/pointeur passés à cette méthode étaient précédemment associés à cet objet par un appel à [CWorkerThread :: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant illustre une implémentation simple de `IWorkerThreadClient::Execute` .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread (classe)](../../atl/reference/cworkerthread-class.md)
