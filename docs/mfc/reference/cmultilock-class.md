---
description: 'En savoir plus sur : classe CMultiLock'
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
ms.openlocfilehash: 1a45c3c302b9f8028061649e2a0d270d47ed58aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331545"
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
|[CMultiLock :: IsLocked](#islocked)|Détermine si un objet de synchronisation spécifique dans le tableau est verrouillé.|
|[CMultiLock :: Lock](#lock)|Attend le tableau d’objets de synchronisation.|
|[CMultiLock :: Unlock](#unlock)|Libère tous les objets de synchronisation détenus.|

## <a name="remarks"></a>Notes

`CMultiLock` n’a pas de classe de base.

Pour utiliser les classes de synchronisation [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md)et [CEvent](../../mfc/reference/cevent-class.md), vous pouvez créer un `CMultiLock` objet ou [CSingleLock](../../mfc/reference/csinglelock-class.md) à attendre et libérer l’objet de synchronisation. `CMultiLock`À utiliser lorsque plusieurs objets peuvent être utilisés à un moment donné. Utilisez `CSingleLock` lorsque vous devez uniquement attendre un objet à la fois.

Pour utiliser un `CMultiLock` objet, commencez par créer un tableau des objets de synchronisation que vous souhaitez attendre. Ensuite, appelez le `CMultiLock` constructeur de l’objet à l’intérieur d’une fonction membre dans la classe de la ressource contrôlée. Appelez ensuite la fonction membre [Lock](#lock) pour déterminer si une ressource est disponible (signalée). Le cas échéant, continuez avec le reste de la fonction membre. Si aucune ressource n’est disponible, patientez pendant un laps de temps spécifié pour la libération d’une ressource ou renvoyez l’erreur. Une fois que l’utilisation d’une ressource est terminée, appelez la fonction [Unlock](#unlock) si l' `CMultiLock` objet doit être réutilisé, ou autorisez la destruction de l' `CMultiLock` objet.

`CMultiLock` les objets sont particulièrement utiles quand un thread a un grand nombre d' `CEvent` objets auxquels il peut répondre. Créez un tableau contenant tous les `CEvent` pointeurs et appelez `Lock` . Cela entraînera l’attente du thread jusqu’à ce que l’un des événements soit signalé.

Pour plus d’informations sur l’utilisation des `CMultiLock` objets, consultez l’article [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CMultiLock`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmt. h

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a> CMultiLock::CMultiLock

Construit un objet `CMultiLock`.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Paramètres

*ppObjects*<br/>
Tableau de pointeurs vers les objets de synchronisation à attendre. Ne peut pas avoir la valeur NULL.

*dwCount*<br/>
Nombre d’objets dans *ppObjects*. Doit être supérieure à 0.

*bInitialLock*<br/>
Spécifie s’il faut tenter d’accéder initialement à l’un des objets fournis.

### <a name="remarks"></a>Notes

Cette fonction est appelée après la création du tableau d’objets de synchronisation à attendre. Elle est généralement appelée à partir du thread qui doit attendre que l’un des objets de synchronisation devienne disponible.

## <a name="cmultilockislocked"></a><a name="islocked"></a> CMultiLock :: IsLocked

Détermine si l’objet spécifié est non signalé (non disponible).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Paramètres

*dwItem*<br/>
Index dans le tableau d’objets correspondant à l’objet dont l’État est en cours d’interrogation.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet spécifié est verrouillé ; Sinon, 0.

## <a name="cmultilocklock"></a><a name="lock"></a> CMultiLock :: Lock

Appelez cette fonction pour accéder à une ou plusieurs des ressources contrôlées par les objets de synchronisation fournis au `CMultiLock` constructeur.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Paramètres

*dwTimeOut*<br/>
Spécifie la durée d’attente de la disponibilité de l’objet de synchronisation (signalé). S’il est infini, `Lock` attend que l’objet soit signalé avant de retourner.

*bWaitForAll*<br/>
Spécifie si tous les objets attendus doivent être signalés en même temps avant de retourner. Si la valeur est FALSe, `Lock` retourne lorsque l’un des objets attendus est signalé.

*dwWakeMask*<br/>
Spécifie d’autres conditions qui sont autorisées à abandonner l’attente. Pour obtenir la liste complète des options disponibles pour ce paramètre, consultez [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Si `Lock` échoue, elle retourne-1. En cas de réussite, elle retourne l’une des valeurs suivantes :

- Entre WAIT_OBJECT_0 et WAIT_OBJECT_0 + (nombre d’objets-1)

   Si *bWaitForAll* a la valeur true, tous les objets sont signalés (disponibles). Si *bWaitForAll* a la valeur false, la valeur de retour-WAIT_OBJECT_0 est l’index dans le tableau d’objets de l’objet signalé (disponible).

- WAIT_OBJECT_0 + (nombre d’objets)

   Un événement spécifié dans *dwWakeMask* est disponible dans la file d’attente d’entrée du thread.

- Entre WAIT_ABANDONED_0 et WAIT_ABANDONED_0 + (nombre d’objets-1)

   Si *bWaitForAll* a la valeur true, tous les objets sont signalés et au moins l’un des objets est un objet mutex abandonné. Si *bWaitForAll* a la valeur false, la valeur de retour-WAIT_ABANDONED_0 est l’index dans le tableau d’objets de l’objet mutex abandonné qui a respecté l’attente.

- WAIT_TIMEOUT

   L’intervalle de délai d’attente spécifié dans *dwTimeOut* a expiré sans l’attente réussie.

### <a name="remarks"></a>Notes

Si *bWaitForAll* a la valeur true, `Lock` renvoie correctement dès que tous les objets de synchronisation sont signalés simultanément. Si *bWaitForAll* a la valeur false, `Lock` le retournera dès qu’un ou plusieurs objets de synchronisation seront signalés.

Si ne `Lock` peut pas être retourné immédiatement, il n’attend pas plus que le nombre de millisecondes spécifié dans le paramètre *dwTimeOut* avant de retourner. Si *dwTimeOut* est infini, ne `Lock` retourne pas tant que l’accès à un objet n’est pas atteint ou qu’une condition spécifiée dans *dwWakeMask* a été remplie. Dans le cas contraire, si `Lock` a pu acquérir un objet de synchronisation, il sera retourné avec succès ; sinon, il retourne un échec.

## <a name="cmultilockunlock"></a><a name="unlock"></a> CMultiLock :: Unlock

Libère l’objet de synchronisation détenu par `CMultiLock` .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Paramètres

*lCount*<br/>
Nombre de décomptes de références à libérer. Doit être supérieure à 0. Si la quantité spécifiée fait que le nombre de l’objet dépasse sa valeur maximale, le nombre n’est pas modifié et la fonction retourne FALSe.

*lPrevCount*<br/>
Pointe vers une variable pour recevoir le nombre précédent de l’objet de synchronisation. Si la valeur est NULL, le nombre précédent n’est pas retourné.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est appelée par le `CMultiLock` destructeur de.

La première forme de `Unlock` tente de déverrouiller l’objet de synchronisation géré par `CMultiLock` . La deuxième forme de `Unlock` tente de déverrouiller les `CSemaphore` objets appartenant à `CMultiLock` . Si `CMultiLock` ne possède pas d' `CSemaphore` objet verrouillé, la fonction retourne la valeur false ; sinon, elle retourne la valeur true. *lCount* et *lpPrevCount* sont exactement les mêmes que les paramètres de [CSingleLock :: Unlock](../../mfc/reference/csinglelock-class.md#unlock). La seconde forme de `Unlock` est rarement applicable aux situations de multiverrouillage.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
