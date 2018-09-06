---
title: Classe de Win32ThreadTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8b481c917292c672711c308ac39c052ed4ea1d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752119"
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

*lpsa*  
Les attributs de sécurité pour le nouveau thread.

*dwStackSize*  
La taille de pile pour le nouveau thread.

*pfnThreadProc*  
La procédure de thread du nouveau thread.

*pvParam*  
Le paramètre à passer à la procédure de thread.

*dwCreationFlags*  
La création d’indicateurs (0 ou CREATE_SUSPENDED).

*pdwThreadId*  
[out] Adresse de la variable DWORD qui, en cas de réussite, reçoit l’ID de thread du thread nouvellement créé.

### <a name="return-value"></a>Valeur de retour

Retourne le handle vers le thread nouvellement créé ou NULL en cas d’échec. Appelez [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) pour obtenir des informations d’erreur étendues.

### <a name="remarks"></a>Notes

Consultez [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) pour plus d’informations sur les paramètres de cette fonction.

Cette fonction appelle `CreateThread` pour créer le thread.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
