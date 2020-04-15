---
title: Win32ThreadTraits Classe
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: 64f02293508894a70f36c29d5032c9ba8f250c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325800"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits Classe

Cette classe fournit la fonction de création pour un thread Windows. Utilisez cette classe si le thread n’utilise pas les fonctions CRT.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class Win32ThreadTraits
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|(Statique) Appelez cette fonction pour créer un thread qui ne doit pas utiliser les fonctions CRT.|

## <a name="remarks"></a>Notes

Les traits de fil sont des classes qui fournissent une fonction de création pour un type particulier de thread. La fonction de création a la même signature et la même sémantique que la fonction Windows [CreateThread.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

Les traits de fil sont utilisés par les classes suivantes :

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Si le thread utilise les fonctions CRT, utilisez [plutôt CRTThreadTraits.](../../atl/reference/crtthreadtraits-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="win32threadtraitscreatethread"></a><a name="createthread"></a>Win32ThreadTraits::CreateThread

Appelez cette fonction pour créer un thread qui ne doit pas utiliser les fonctions CRT.

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>Paramètres

*lpsa lpsa*<br/>
Les attributs de sécurité pour le nouveau thread.

*dwStackSize*<br/>
La taille de pile pour le nouveau thread.

*pfnThreadProc*<br/>
La procédure de fil du nouveau thread.

*pvParam pvParam*<br/>
Le paramètre à transmettre à la procédure de thread.

*dwCreationFlags dwCreationFlags dwCreationFlags*<br/>
Les drapeaux de création (0 ou CREATE_SUSPENDED).

*pdwThreadId*<br/>
[out] Adresse de la variable DWORD qui, sur le succès, reçoit l’ID de fil du fil nouvellement créé.

### <a name="return-value"></a>Valeur de retour

Retourne la poignée au fil nouvellement créé ou NULL sur l’échec. Appelez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour obtenir des informations d’erreur étendues.

### <a name="remarks"></a>Notes

Voir [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) pour plus d’informations sur les paramètres de cette fonction.

Cette fonction `CreateThread` appelle à créer le thread.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
