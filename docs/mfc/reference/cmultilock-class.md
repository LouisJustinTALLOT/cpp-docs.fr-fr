---
title: CMultiLock, classe
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: a051c6a510c53ac0c7c0a6efd8b4b5720080b264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319711"
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
|[CMultiLock::Lock](#lock)|Attend sur la gamme d’objets de synchronisation.|
|[CMultiLock::Unlock](#unlock)|Libère tous les objets de synchronisation possédés.|

## <a name="remarks"></a>Notes

`CMultiLock`n’a pas de classe de base.

Pour utiliser les classes de synchronisation [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), et `CMultiLock` [CEvent](../../mfc/reference/cevent-class.md), vous pouvez créer un objet ou [CSingleLock](../../mfc/reference/csinglelock-class.md) pour attendre et libérer l’objet de synchronisation. Utilisez `CMultiLock` quand il ya plusieurs objets que vous pouvez utiliser à un moment donné. Utilisez `CSingleLock` lorsque vous n’avez qu’à attendre sur un objet à la fois.

Pour utiliser `CMultiLock` un objet, créez d’abord un tableau des objets de synchronisation que vous souhaitez attendre. Ensuite, appelez `CMultiLock` le constructeur de l’objet à l’intérieur d’une fonction membre dans la classe de la ressource contrôlée. Appelez ensuite la fonction membre [Lock](#lock) pour déterminer si une ressource est disponible (signalée). Si l’on l’est, continuez avec le reste de la fonction membre. Si aucune ressource n’est disponible, attendez un délai précis pour qu’une ressource soit libérée ou que la défaillance du retour soit. Une fois l’utilisation d’une ressource terminée, soit appelez la fonction `CMultiLock` [Déverrouiller](#unlock) si l’objet `CMultiLock` doit être utilisé à nouveau, soit laissez l’objet être détruit.

`CMultiLock`les objets sont plus utiles lorsqu’un thread a un grand nombre d’objets `CEvent` à qui il peut répondre. Créez un tableau `CEvent` contenant tous les `Lock`pointeurs, et appelez . Cela fera attendre le fil jusqu’à ce que l’un des événements est signalé.

Pour plus d’informations `CMultiLock` sur la façon d’utiliser des objets, voir l’article [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CMultiLock`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmt.h

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a>CMultiLock::CMultiLock

Construit un objet `CMultiLock`.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Paramètres

*ppObjects*<br/>
Array de pointeurs aux objets de synchronisation à attendre. Ne peut pas avoir la valeur NULL.

*dwCompte*<br/>
Nombre d’objets en *ppObjects*. Doit être supérieure à 0.

*bInitialLock (en)*<br/>
Précise s’il faut d’abord tenter d’accéder à l’un des objets fournis.

### <a name="remarks"></a>Notes

Cette fonction est appelée après la création de la gamme d’objets de synchronisation à attendre. Il est généralement appelé de l’intérieur du fil qui doit attendre que l’un des objets de synchronisation devienne disponible.

## <a name="cmultilockislocked"></a><a name="islocked"></a>CMultiLock::IsLocked

Détermine si l’objet spécifié n’est pas signé (indisponible).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Paramètres

*dwItem dwItem*<br/>
L’index dans la gamme d’objets correspondant à l’objet dont l’état est interrogé.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet spécifié est verrouillé; sinon 0.

## <a name="cmultilocklock"></a><a name="lock"></a>CMultiLock::Lock

Appelez cette fonction pour accéder à une ou plusieurs des ressources contrôlées `CMultiLock` par les objets de synchronisation fournis au constructeur.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Paramètres

*dwTimeOut (en)*<br/>
Spécifie le temps d’attente pour que l’objet de synchronisation soit disponible (signalé). Si INFINITE, `Lock` attendra que l’objet soit signalé avant de revenir.

*bWaitForAll*<br/>
Précise si tous les objets attendus doivent être signalés en même temps avant de revenir. Si FALSE, `Lock` revient quand l’un des objets attendus est signalé.

*dwWakeMask*<br/>
Spécifie d’autres conditions qui sont autorisées à interrompre l’attente. Pour une liste complète des options disponibles pour ce paramètre, voir [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

En `Lock` cas d’échec, il revient - 1. En cas de succès, il renvoie l’une des valeurs suivantes :

- Entre WAIT_OBJECT_0 et WAIT_OBJECT_0 (nombre d’objets - 1)

   Si *bWaitForAll* est VRAI, tous les objets sont signalés (disponibles). Si *bWaitForAll* est FALSE, la valeur de retour - WAIT_OBJECT_0 est l’index dans la gamme d’objets de l’objet qui est signalé (disponible).

- WAIT_OBJECT_0 (nombre d’objets)

   Un événement spécifié dans *dwWakeMask* est disponible dans la file d’attente d’entrée du thread.

- Entre WAIT_ABANDONED_0 et WAIT_ABANDONED_0 (nombre d’objets - 1)

   Si *bWaitForAll* est VRAI, tous les objets sont signalés, et au moins un des objets est un objet mutex abandonné. Si *bWaitForAll* est FALSE, la valeur de retour - WAIT_ABANDONED_0 est l’index dans la gamme d’objets de l’objet mutex abandonné qui a satisfait l’attente.

- WAIT_TIMEOUT

   L’intervalle de délai spécifié dans *dwTimeOut* a expiré sans que l’attente ne réussisse.

### <a name="remarks"></a>Notes

Si *bWaitForAll* est `Lock` VRAI, reviendra avec succès dès que tous les objets de synchronisation seront signalés simultanément. Si *bWaitForAll* est `Lock` FALSE, reviendra dès qu’un ou plusieurs des objets de synchronisation seront signalés.

S’il `Lock` n’est pas en mesure de revenir immédiatement, il n’attendra pas plus que le nombre de millisecondes spécifiées dans le paramètre *dwTimeOut* avant de revenir. Si *dwTimeOut* est `Lock` INFINITE, ne reviendra pas jusqu’à ce que l’accès à un objet soit gagné ou qu’une condition spécifiée dans *dwWakeMask* ait été remplie. Sinon, `Lock` si elle était en mesure d’acquérir un objet de synchronisation, elle reviendra avec succès; sinon, il reviendra l’échec.

## <a name="cmultilockunlock"></a><a name="unlock"></a>CMultiLock::Unlock

Libère l’objet de `CMultiLock`synchronisation appartenant à .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Paramètres

*lCompte*<br/>
Nombre de comptes de référence à libérer. Doit être supérieure à 0. Si le montant spécifié ferait dépasser le nombre de l’objet, le nombre n’est pas modifié et la fonction renvoie FALSE.

*lPrevCompte*<br/>
Points à une variable pour recevoir le compte précédent pour l’objet de synchronisation. Si NULL, le compte précédent n’est pas retourné.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est `CMultiLock`appelée par le destructeur de 's.

La première `Unlock` forme d’essais pour débloquer `CMultiLock`l’objet de synchronisation géré par . La deuxième `Unlock` forme d’essayer de déverrouiller les `CSemaphore` objets appartenant à `CMultiLock`. S’il `CMultiLock` ne `CSemaphore` possède aucun objet verrouillé, la fonction renvoie FALSE; sinon, il revient VRAI. *lCount* et *lpPrevCount* sont exactement les mêmes que les paramètres de [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). La deuxième `Unlock` forme de est rarement applicable aux situations multiblos.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
