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
ms.openlocfilehash: 6a68f25f153a0ad2cf42ebfaa374ff63c5746fcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326298"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient Interface

`IWorkerThreadClient`est l’interface implémentée par les clients de la classe [CWorkerThread.](../../atl/reference/cworkerthread-class.md)

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CloseHandle (closeHandle)](#closehandle)|Implémentez cette méthode pour fermer la poignée associée à cet objet.|
|[Execute](#execute)|Implémentez cette méthode pour exécuter le code lorsque la poignée associée à cet objet devient signalée.|

## <a name="remarks"></a>Notes

Implémentez cette interface lorsque vous avez du code qui doit s’exécuter sur un thread de travailleur en réponse à une poignée qui devient signalée.

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle

Implémentez cette méthode pour fermer la poignée associée à cet objet.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Paramètres

*hHandle*<br/>
La poignée à fermer.

### <a name="return-value"></a>Valeur de retour

Retour S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

La poignée passée à cette méthode était auparavant associée à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant montre `IWorkerThreadClient::CloseHandle`une simple implémentation de .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Exécuter

Implémentez cette méthode pour exécuter le code lorsque la poignée associée à cet objet devient signalée.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Paramètres

*dwParam dwParam*<br/>
Le paramètre de l’utilisateur.

*hObject*<br/>
La poignée qui est devenue signalée.

### <a name="return-value"></a>Valeur de retour

Retour S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

La poignée et DWORD / pointeur passé à cette méthode ont été précédemment associés à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant montre `IWorkerThreadClient::Execute`une simple implémentation de .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[Classe CWorkerThread](../../atl/reference/cworkerthread-class.md)
