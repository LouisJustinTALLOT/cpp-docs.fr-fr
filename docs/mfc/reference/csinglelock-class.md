---
description: 'En savoir plus sur : CSingleLock, classe'
title: CSingleLock (classe)
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 7fa4fe32ce38bf47ede1b6ac133d1a057907f9c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342854"
---
# <a name="csinglelock-class"></a>CSingleLock (classe)

Représente le mécanisme de contrôle d'accès utilisé dans le contrôle de l'accès à une ressource dans un programme multithread.

## <a name="syntax"></a>Syntaxe

```
class CSingleLock
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSingleLock :: CSingleLock](#csinglelock)|Construit un objet `CSingleLock`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSingleLock :: IsLocked](#islocked)|Détermine si l’objet est verrouillé.|
|[CSingleLock :: Lock](#lock)|Attend un objet de synchronisation.|
|[CSingleLock :: Unlock](#unlock)|Libère un objet de synchronisation.|

## <a name="remarks"></a>Notes

`CSingleLock` n’a pas de classe de base.

Afin d’utiliser les classes de synchronisation [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)et [CEvent](../../mfc/reference/cevent-class.md), vous devez créer un `CSingleLock` objet ou [CMultiLock](../../mfc/reference/cmultilock-class.md) pour attendre et libérer l’objet de synchronisation. Utilisez `CSingleLock` lorsque vous devez uniquement attendre un objet à la fois. `CMultiLock`À utiliser lorsque plusieurs objets peuvent être utilisés à un moment donné.

Pour utiliser un `CSingleLock` objet, appelez son constructeur à l’intérieur d’une fonction membre dans la classe de la ressource contrôlée. Appelez ensuite la fonction membre [IsLocked](#islocked) pour déterminer si la ressource est disponible. Si c’est le cas, continuez avec le reste de la fonction membre. Si la ressource n’est pas disponible, patientez pendant un laps de temps spécifié pour la libération de la ressource ou renvoyez l’erreur. Une fois que l’utilisation de la ressource est terminée, appelez la fonction [Unlock](#unlock) si l' `CSingleLock` objet doit être réutilisé, ou autorisez la `CSingleLock` destruction de l’objet.

`CSingleLock` les objets nécessitent la présence d’un objet dérivé de [CSyncObject](../../mfc/reference/csyncobject-class.md). Il s’agit généralement d’un membre de données de la classe de la ressource contrôlée. Pour plus d’informations sur l’utilisation des `CSingleLock` objets, consultez l’article [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CSingleLock`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmt. h

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a> CSingleLock :: CSingleLock

Construit un objet `CSingleLock`.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Pointe vers l’objet de synchronisation auquel accéder. Ne peut pas avoir la valeur NULL.

*bInitialLock*<br/>
Spécifie s’il faut tenter d’accéder initialement à l’objet fourni.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée à partir d’une fonction membre d’accès de la ressource contrôlée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a> CSingleLock :: IsLocked

Détermine si l’objet associé à l' `CSingleLock` objet est non signalé (non disponible).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet est verrouillé ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a> CSingleLock :: Lock

Appelez cette fonction pour accéder à la ressource contrôlée par l’objet de synchronisation fourni au `CSingleLock` constructeur.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Paramètres

*dwTimeOut*<br/>
Spécifie la durée d’attente de la disponibilité de l’objet de synchronisation (signalé). S’il est infini, `Lock` attend que l’objet soit signalé avant de retourner.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Si l’objet de synchronisation est signalé, `Lock` retourne avec succès et le thread est propriétaire de l’objet. Si l’objet de synchronisation est non signalé (non disponible), `Lock` attend que l’objet de synchronisation soit signalé jusqu’au nombre de millisecondes spécifié dans le paramètre *dwTimeOut* . Si l’objet de synchronisation n’a pas été signalé dans le laps de temps spécifié, `Lock` retourne une erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a> CSingleLock :: Unlock

Libère l’objet de synchronisation détenu par `CSingleLock` .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Paramètres

*lCount*<br/>
Nombre d’accès à libérer. Doit être supérieure à 0. Si la quantité spécifiée fait que le nombre de l’objet dépasse sa valeur maximale, le nombre n’est pas modifié et la fonction retourne FALSe.

*lPrevCount*<br/>
Pointe vers une variable pour recevoir le nombre précédent de l’objet de synchronisation. Si la valeur est NULL, le nombre précédent n’est pas retourné.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est appelée par le `CSingleLock` destructeur de.

Si vous devez libérer plus d’un nombre d’accès d’un sémaphore, utilisez la deuxième forme de `Unlock` et spécifiez le nombre d’accès à libérer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock, classe](../../mfc/reference/cmultilock-class.md)
