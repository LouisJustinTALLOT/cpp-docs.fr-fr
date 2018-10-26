---
title: CMultiLock, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 097f6173faad4f99f64c5dac45e2a0d1292a07eb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076358"
---
# <a name="cmultilock-class"></a>CMultiLock, classe

Représente le mécanisme de contrôle d'accès utilisé pour accéder aux ressources dans un programme multithread.

## <a name="syntax"></a>Syntaxe

```
class CMultiLock
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|Construit un objet `CMultiLock`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMultiLock::IsLocked](#islocked)|Détermine si un objet de synchronisation spécifique dans le tableau est verrouillé.|
|[CMultiLock::Lock](#lock)|Attentes sur le tableau d’objets de synchronisation.|
|[CMultiLock::Unlock](#unlock)|Libère tous les objets détenus de synchronisation.|

## <a name="remarks"></a>Notes

`CMultiLock` n’a pas d’une classe de base.

Pour utiliser les classes de synchronisation [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), et [CEvent](../../mfc/reference/cevent-class.md), vous pouvez créer un `CMultiLock` ou [CSingleLock](../../mfc/reference/csinglelock-class.md)objet attendent et libérer l’objet de synchronisation. Utiliser `CMultiLock` lorsqu’il existe plusieurs objets que vous pouvez utiliser à un moment donné. Utilisez `CSingleLock` lorsque vous devez uniquement pour l’attente sur un seul objet à la fois.

Pour utiliser un `CMultiLock` d’objet, commencez par créer un tableau d’objets de synchronisation que vous souhaitez attendre. Ensuite, appelez le `CMultiLock` constructeur de l’objet à l’intérieur d’une fonction membre de classe de la ressource contrôlée. Appelez ensuite la [verrou](#lock) fonction membre pour déterminer si une ressource est disponible (signalé). Si un est le cas, continuez avec le reste de la fonction membre. Si aucune ressource n’est disponible, attendez un laps de temps pour une ressource doit être publié ou renvoient une erreur. Une fois que l’utilisation d’une ressource est terminée, vous devez soit appeler le [Unlock](#unlock) fonctionner si le `CMultiLock` objet doit être utilisé à nouveau, ou autoriser le `CMultiLock` objet à détruire.

`CMultiLock` les objets sont particulièrement utiles lorsqu’un thread possède un grand nombre de `CEvent` il peut répondre à des objets. Créer un tableau contenant tous les `CEvent` pointeurs, puis appelez `Lock`. Cela entraîne le thread à attendre jusqu'à ce que l’un des événements est signalé.

Pour plus d’informations sur l’utilisation `CMultiLock` objets, consultez l’article [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CMultiLock`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxmt.h

##  <a name="cmultilock"></a>  CMultiLock::CMultiLock

Construit un objet `CMultiLock`.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Paramètres

*ppObjects*<br/>
Tableau de pointeurs vers les objets de synchronisation pour être attendue. Ne peut pas être Null.

*dwCount*<br/>
Nombre d’objets dans *ppObjects*. Doit être supérieure à 0.

*bInitialLock*<br/>
Spécifie s’il faut initialement que vous tentez d’accéder à tous les objets fournis.

### <a name="remarks"></a>Notes

Cette fonction est appelée après la création d’un tableau d’objets de synchronisation pour se mettre en attente. Elle est généralement appelée dans le thread doit attendre pour un des objets de synchronisation à la disposition.

##  <a name="islocked"></a>  CMultiLock::IsLocked

Détermine si l’objet spécifié est "non signalé" (non disponible).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Paramètres

*dwItem*<br/>
L’index dans le tableau d’objets correspondant à l’objet dont l’état est en cours d’interrogation.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet spécifié est verrouillé ; sinon 0.

##  <a name="lock"></a>  CMultiLock::Lock

Appelez cette fonction pour accéder à un ou plusieurs des ressources contrôlées par les objets de synchronisation fournis à la `CMultiLock` constructeur.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Paramètres

*dwTimeOut*<br/>
Spécifie la quantité de temps d’attente pour l’objet de synchronisation soit disponible (signalé). Si elle est infinie, `Lock` attendra jusqu'à ce que l’objet est signalé avant de retourner.

*bWaitForAll*<br/>
Spécifie si tous les objets a attendu sur doivent être signalés en même temps avant de retourner. Si la valeur est FALSE, `Lock` renverra lorsque l’un des objets attendu est signalé.

*dwWakeMask*<br/>
Spécifie les autres conditions qui sont autorisées à abandonner l’attente. Pour obtenir une liste complète des options disponibles pour ce paramètre, consultez [MsgWaitForMultipleObjects](/windows/desktop/api/winuser/nf-winuser-msgwaitformultipleobjects) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Si `Lock` échoue, elle retourne - 1. Si l’opération réussit, elle retourne une des valeurs suivantes :

- Entre WAIT_OBJECT_0 et WAIT_OBJECT_0 + (nombre d’objets - 1)

   Si *bWaitForAll* a la valeur TRUE, tous les objets sont signalés (disponible). Si *bWaitForAll* est FALSE, la valeur de retour - WAIT_OBJECT_0 est l’index dans le tableau d’objets de l’objet qui est signalé (disponible).

- WAIT_OBJECT_0 + (nombre d’objets)

   Un événement spécifié dans *dwWakeMask* est disponible dans la file d’entrée du thread.

- Entre WAIT_ABANDONED_0 et WAIT_ABANDONED_0 + (nombre d’objets - 1)

   Si *bWaitForAll* est TRUE, tous les objets sont signalés, et au moins un des objets est un objet mutex abandonné. Si *bWaitForAll* est FALSE, la valeur de retour - WAIT_ABANDONED_0 est l’index dans le tableau d’objets de l’objet mutex abandonné ayant respecté l’attente.

- WAIT_TIMEOUT

   L’intervalle de délai d’expiration spécifié dans *dwTimeOut* expiré sans l’attente qui suit.

### <a name="remarks"></a>Notes

Si *bWaitForAll* a la valeur TRUE, `Lock` renvoie correctement dès que tous les objets de synchronisation soient signalés simultanément. Si *bWaitForAll* est FALSE, `Lock` retournera dès qu’un ou plusieurs des objets de synchronisation sont signalé.

Si `Lock` n’est pas en mesure de retourner immédiatement, il devra attendre pas plus que le nombre de millisecondes spécifié dans le *dwTimeOut* paramètre avant de retourner. Si *dwTimeOut* est INFINITE, `Lock` reviendra pas avant que l’accès à un objet est acquise ou une condition spécifiée dans *dwWakeMask* a été remplie. Sinon, si `Lock` a été en mesure d’acquérir un objet de synchronisation, elle retournera avec succès ; dans le cas contraire, elle retournera l’échec.

##  <a name="unlock"></a>  CMultiLock::Unlock

Libère l’objet de synchronisation appartenant `CMultiLock`.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Paramètres

*lCount*<br/>
Nombre de référence du nombre de mise en production. Doit être supérieure à 0. Si la quantité spécifiée peut provoquer le nombre de l’objet à dépasser sa valeur maximale, le nombre n’est pas modifié et la fonction retourne FALSE.

*lPrevCount*<br/>
Pointe vers une variable devant recevoir le nombre précédent pour l’objet de synchronisation. Si NULL, le nombre précédent n’est pas retourné.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est appelée par `CMultiLock`du destructeur.

La première forme de `Unlock` tente de déverrouiller l’objet de synchronisation géré par `CMultiLock`. La deuxième forme de `Unlock` tente de déverrouiller le `CSemaphore` objets possédés par `CMultiLock`. Si `CMultiLock` ne possède pas les verrouillé `CSemaphore` objet, la fonction retourne FALSE ; sinon, elle retourne la valeur TRUE. *lCount* et *lpPrevCount* sont exactement les mêmes que les paramètres de [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). La deuxième forme de `Unlock` est rarement applicable aux situations multilock.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

