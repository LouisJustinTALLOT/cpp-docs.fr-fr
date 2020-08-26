---
title: Interface IThreadPoolConfig
ms.date: 11/04/2016
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
ms.openlocfilehash: cba82055c292fc966dc2328773cce4aa64d45a64
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835426"
---
# <a name="ithreadpoolconfig-interface"></a>Interface IThreadPoolConfig

Cette interface fournit des méthodes pour configurer un pool de threads.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[GetSize](#getsize)|Appelez cette méthode pour connaître le nombre de threads dans le pool.|
|[GetTimeout](#gettimeout)|Appelez cette méthode pour obtenir la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.|
|[SetSize](#setsize)|Appelez cette méthode pour définir le nombre de threads dans le pool.|
|[SetTimeout](#settimeout)|Appelez cette méthode pour définir la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.|

## <a name="remarks"></a>Notes

Cette interface est implémentée par [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil. h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a> IThreadPoolConfig :: est à obtenir

Appelez cette méthode pour connaître le nombre de threads dans le pool.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Paramètres

*pnNumThreads*<br/>
à Adresse de la variable qui, en cas de réussite, reçoit le nombre de threads dans le pool.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a> IThreadPoolConfig::GetTimeout

Appelez cette méthode pour obtenir la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Paramètres

*pdwMaxWait*<br/>
à Adresse de la variable qui, en cas de réussite, reçoit la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig :: de](#getsize).

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a> IThreadPoolConfig :: configure

Appelez cette méthode pour définir le nombre de threads dans le pool.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Paramètres

*nNumThreads*<br/>
Nombre demandé de threads dans le pool.

Si *nNumThreads* est négatif, sa valeur absolue est multipliée par le nombre de processeurs de l’ordinateur pour connaître le nombre total de threads.

Si *nNumThreads* est égal à zéro, ATLS_DEFAULT_THREADSPERPROC sera multiplié par le nombre de processeurs de l’ordinateur pour connaître le nombre total de threads.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig :: de](#getsize).

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a> IThreadPoolConfig :: SetTimeout

Appelez cette méthode pour définir la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Paramètres

*dwMaxWait*<br/>
Durée maximale demandée en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig :: de](#getsize).

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[CThreadPool (classe)](../../atl/reference/cthreadpool-class.md)
