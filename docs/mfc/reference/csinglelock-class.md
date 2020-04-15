---
title: CSingleLock, classe
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
ms.openlocfilehash: 231397228d94e58665602453b5d377571e24a967
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318273"
---
# <a name="csinglelock-class"></a>CSingleLock, classe

Représente le mécanisme de contrôle d'accès utilisé dans le contrôle de l'accès à une ressource dans un programme multithread.

## <a name="syntax"></a>Syntaxe

```
class CSingleLock
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Construit un objet `CSingleLock`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSingleLock::IsLocked](#islocked)|Détermine si l’objet est verrouillé.|
|[CSingleLock::Lock](#lock)|Attend sur un objet de synchronisation.|
|[CSingleLock::Unlock](#unlock)|Libère un objet de synchronisation.|

## <a name="remarks"></a>Notes

`CSingleLock`n’a pas de classe de base.

Afin d’utiliser les classes de synchronisation [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), `CSingleLock` et [CEvent](../../mfc/reference/cevent-class.md), vous devez créer soit un ou [CMultiLock](../../mfc/reference/cmultilock-class.md) objet d’attendre et de libérer l’objet de synchronisation. Utilisez `CSingleLock` lorsque vous n’avez qu’à attendre sur un objet à la fois. Utilisez `CMultiLock` quand il ya plusieurs objets que vous pouvez utiliser à un moment donné.

Pour utiliser `CSingleLock` un objet, appelez son constructeur à l’intérieur d’une fonction membre dans la classe de la ressource contrôlée. Appelez ensuite la fonction membre [IsLocked](#islocked) pour déterminer si la ressource est disponible. Si c’est le cas, continuez avec le reste de la fonction membre. Si la ressource n’est pas disponible, attendez un délai spécifié pour que la ressource soit libérée, soit en cas de défaillance du retour. Une fois l’utilisation de la ressource terminée, soit appelez la fonction `CSingleLock` [Déverrouiller](#unlock) si l’objet `CSingleLock` doit être utilisé à nouveau, ou permettre à l’objet d’être détruit.

`CSingleLock`d’objets nécessitent la présence d’un objet dérivé de [CSyncObject](../../mfc/reference/csyncobject-class.md). Il s’agit généralement d’un membre des données de la catégorie de la ressource contrôlée. Pour plus d’informations `CSingleLock` sur la façon d’utiliser des objets, voir l’article [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CSingleLock`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmt.h

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a>CSingleLock::CSingleLock

Construit un objet `CSingleLock`.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Points à l’objet de synchronisation à accéder. Ne peut pas avoir la valeur NULL.

*bInitialLock (en)*<br/>
Précise s’il faut d’abord tenter d’accéder à l’objet fourni.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée à partir d’une fonction membre d’accès de la ressource contrôlée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a>CSingleLock::IsLocked

Détermine si l’objet `CSingleLock` associé à l’objet n’est pas asigné (indisponible).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet est verrouillé; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a>CSingleLock::Lock

Appelez cette fonction pour accéder à la ressource contrôlée par `CSingleLock` l’objet de synchronisation fourni au constructeur.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Paramètres

*dwTimeOut (en)*<br/>
Spécifie le temps d’attente pour que l’objet de synchronisation soit disponible (signalé). Si INFINITE, `Lock` attendra que l’objet soit signalé avant de revenir.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Si l’objet de synchronisation `Lock` est signalé, reviendra avec succès et le thread possède maintenant l’objet. Si l’objet de synchronisation n’est pas `Lock` signé (indisponible), attendra que l’objet de synchronisation soit signalé jusqu’au nombre de millisecondes spécifiées dans le paramètre *dwTimeOut.* Si l’objet de synchronisation n’est pas signalé `Lock` dans le laps de temps spécifié, l’échec des retours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a>CSingleLock::Unlock

Libère l’objet de `CSingleLock`synchronisation appartenant à .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Paramètres

*lCompte*<br/>
Nombre d’accès à la libération. Doit être supérieure à 0. Si le montant spécifié ferait dépasser le nombre de l’objet, le nombre n’est pas modifié et la fonction renvoie FALSE.

*lPrevCompte*<br/>
Indique une variable pour recevoir le nombre précédent de l’objet de synchronisation. Si NULL, le compte précédent n’est pas retourné.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est `CSingleLock`appelée par le destructeur de 's.

Si vous avez besoin de libérer plus d’un nombre d’accès d’un sémaphore, utilisez la deuxième forme et `Unlock` spécifiez le nombre d’accès à la libération.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock, classe](../../mfc/reference/cmultilock-class.md)
