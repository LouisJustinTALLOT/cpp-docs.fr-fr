---
title: Crtthreadtraits, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 676d14b1027cbc9df68e4be26a9a1451a29d8c37
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204310"
---
# <a name="crtthreadtraits-class"></a>Crtthreadtraits, classe
Cette classe fournit la fonction de création d’un thread de CRT. Utilisez cette classe si le thread utilise des fonctions CRT.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CRTThreadTraits
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CRTThreadTraits::CreateThread](#createthread)|(Statique) Appelez cette fonction pour créer un thread qui utilise des fonctions CRT.|  
  
## <a name="remarks"></a>Notes  
 Caractéristiques de thread sont des classes qui fournissent une fonction de création d’un type particulier de thread. La fonction de création a la même signature et la même sémantique que le Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) (fonction).  
  
 Caractéristiques de thread sont utilisés par les classes suivantes :  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Si le thread n’utilisera pas les fonctions CRT, utilisez [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) à la place.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
  
##  <a name="createthread"></a>  CRTThreadTraits::CreateThread  
 Appelez cette fonction pour créer un thread qui utilise des fonctions CRT.  
  
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
  
 Cette fonction appelle [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) pour créer le thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
