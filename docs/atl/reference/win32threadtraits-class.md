---
title: Classe de Win32ThreadTraits
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
ms.openlocfilehash: cae5faea7938918da2656e21648282c1a2e1a66d
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503767"
---
# <a name="win32threadtraits-class"></a>Classe de Win32ThreadTraits

Cette classe fournit la fonction de création d’un thread Windows. Utilisez cette classe si le thread ne doit pas utiliser de fonctions CRT.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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

Caractéristiques de thread sont des classes qui fournissent une fonction de création d’un type particulier de thread. La fonction de création a la même signature et la même sémantique que le Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) (fonction).

Caractéristiques de thread sont utilisés par les classes suivantes :

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Si le thread sera des fonctions CRT, utilisez [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) à la place.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread

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

*lpsa*<br/>
Les attributs de sécurité pour le nouveau thread.

*dwStackSize*<br/>
La taille de pile pour le nouveau thread.

*pfnThreadProc*<br/>
La procédure de thread du nouveau thread.

*pvParam*<br/>
Le paramètre à passer à la procédure de thread.

*dwCreationFlags*<br/>
La création d’indicateurs (0 ou CREATE_SUSPENDED).

*pdwThreadId*<br/>
[out] Adresse de la variable DWORD qui, en cas de réussite, reçoit l’ID de thread du thread nouvellement créé.

### <a name="return-value"></a>Valeur de retour

Retourne le handle vers le thread nouvellement créé ou NULL en cas d’échec. Appelez [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour obtenir des informations d’erreur étendues.

### <a name="remarks"></a>Notes

Consultez [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) pour plus d’informations sur les paramètres de cette fonction.

Cette fonction appelle `CreateThread` pour créer le thread.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
