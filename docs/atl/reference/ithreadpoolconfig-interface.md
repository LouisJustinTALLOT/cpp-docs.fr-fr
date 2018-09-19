---
title: IThreadPoolConfig, Interface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 156a0a827a67e80369ca8b834b62bcf0e431ab14
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076344"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig, Interface

Cette interface fournit des méthodes pour configurer un pool de threads.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[GetSize](#getsize)|Appelez cette méthode pour obtenir le nombre de threads dans le pool.|
|[GetTimeout](#gettimeout)|Appelez cette méthode pour obtenir la durée maximale en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.|
|[SetSize](#setsize)|Appelez cette méthode pour définir le nombre de threads dans le pool.|
|[SetTimeout](#settimeout)|Appelez cette méthode pour définir le temps maximal en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.|

## <a name="remarks"></a>Notes

Cette interface est implémentée par [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

##  <a name="getsize"></a>  IThreadPoolConfig::GetSize

Appelez cette méthode pour obtenir le nombre de threads dans le pool.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Paramètres

*pnNumThreads*<br/>
[out] Adresse de la variable qui, en cas de réussite, reçoit le nombre de threads dans le pool.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout

Appelez cette méthode pour obtenir la durée maximale en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Paramètres

*pdwMaxWait*<br/>
[out] Adresse de la variable recevant, en cas de réussite, la durée maximale en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig::GetSize](#getsize).

##  <a name="setsize"></a>  IThreadPoolConfig::SetSize

Appelez cette méthode pour définir le nombre de threads dans le pool.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Paramètres

*nNumThreads*<br/>
Le nombre demandé de threads dans le pool.

Si *nNumThreads* est négatif, sa valeur absolue sera multipliée par le nombre de processeurs sur l’ordinateur pour obtenir le nombre total de threads.

Si *nNumThreads* est égal à zéro, ATLS_DEFAULT_THREADSPERPROC sera multiplié par le nombre de processeurs sur l’ordinateur pour obtenir le nombre total de threads.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig::GetSize](#getsize).

##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout

Appelez cette méthode pour définir le temps maximal en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Paramètres

*dwMaxWait*<br/>
La durée maximale demandée en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[CThreadPool, classe](../../atl/reference/cthreadpool-class.md)
