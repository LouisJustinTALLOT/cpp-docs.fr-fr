---
description: 'En savoir plus sur : classe CRTThreadTraits'
title: CRTThreadTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: 30f9f435ad447a33d513379ceee0d254f48dfec8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140840"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits, classe

Cette classe fournit la fonction de création d’un thread CRT. Utilisez cette classe si le thread utilise des fonctions CRT.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CRTThreadTraits
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRTThreadTraits :: CreateThread](#createthread)|Statique Appelez cette fonction pour créer un thread qui peut utiliser des fonctions CRT.|

## <a name="remarks"></a>Notes

Les caractéristiques de thread sont des classes qui fournissent une fonction de création pour un type particulier de thread. La fonction de création a la même signature et la même sémantique que la fonction Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) .

Les caractéristiques de thread sont utilisées par les classes suivantes :

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Si le thread n’utilise pas de fonctions CRT, utilisez [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) à la place.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="crtthreadtraitscreatethread"></a><a name="createthread"></a> CRTThreadTraits :: CreateThread

Appelez cette fonction pour créer un thread qui peut utiliser des fonctions CRT.

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
Attributs de sécurité pour le nouveau thread.

*dwStackSize*<br/>
Taille de la pile pour le nouveau thread.

*pfnThreadProc*<br/>
Procédure de thread du nouveau thread.

*pvParam*<br/>
Paramètre à passer à la procédure de thread.

*dwCreationFlags*<br/>
Indicateurs de création (0 ou CREATE_SUSPENDED).

*pdwThreadId*<br/>
à Adresse de la variable DWORD qui, en cas de réussite, reçoit l’ID de thread du thread nouvellement créé.

### <a name="return-value"></a>Valeur renvoyée

Retourne le handle du thread nouvellement créé ou NULL en cas d’échec. Appelez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour recevoir les informations d’erreur étendues.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les paramètres de cette fonction, consultez [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) .

Cette fonction appelle [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) pour créer le thread.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
