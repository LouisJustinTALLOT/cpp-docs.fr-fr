---
title: IThreadPoolConfig Interface
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
ms.openlocfilehash: e4b90534fa89ef2aeffe4cd682d92efc16452487
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326359"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig Interface

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

|||
|-|-|
|[GetSize](#getsize)|Appelez cette méthode pour obtenir le nombre de threads dans la piscine.|
|[GetTimeout (en)](#gettimeout)|Appelez cette méthode pour obtenir le temps maximum en millisecondes que le pool de thread attendra pour un thread pour s’éteindre.|
|[SetSize SetSize SetSize SetS](#setsize)|Appelez cette méthode pour définir le nombre de threads dans le pool.|
|[Settimeout](#settimeout)|Appelez cette méthode pour définir le temps maximum en millisecondes que le pool de thread attendra qu’un fil s’arrête.|

## <a name="remarks"></a>Notes

Cette interface est implémentée par [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPoolConfig::GetSize

Appelez cette méthode pour obtenir le nombre de threads dans la piscine.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Paramètres

*pnNumThreads (en)*<br/>
[out] Adresse de la variable qui, sur le succès, reçoit le nombre de threads dans le pool.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPoolConfig::GetTimeout

Appelez cette méthode pour obtenir le temps maximum en millisecondes que le pool de thread attendra pour un thread pour s’éteindre.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Paramètres

*pdwMaxWait*<br/>
[out] Adresse de la variable qui, sur le succès, reçoit le temps maximum en millisecondes que le pool de thread attendra pour un thread pour s’éteindre.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="example"></a>Exemple

Voir [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPoolConfig::SetSize

Appelez cette méthode pour définir le nombre de threads dans le pool.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Paramètres

*nNumThreads (en)*<br/>
Le nombre demandé de fils dans la piscine.

Si *nNumThreads* est négatif, sa valeur absolue sera multipliée par le nombre de processeurs dans la machine pour obtenir le nombre total de threads.

Si *nNumThreads* est nul, ATLS_DEFAULT_THREADSPERPROC sera multipliée par le nombre de processeurs dans la machine pour obtenir le nombre total de threads.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="example"></a>Exemple

Voir [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPoolConfig::SetTimeout

Appelez cette méthode pour définir le temps maximum en millisecondes que le pool de thread attendra qu’un fil s’arrête.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Paramètres

*dwMaxWait*<br/>
Le temps maximum demandé en millisecondes que le pool de fil attendra pour un fil pour s’arrêter.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="example"></a>Exemple

Voir [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[Classe CThreadPool](../../atl/reference/cthreadpool-class.md)
