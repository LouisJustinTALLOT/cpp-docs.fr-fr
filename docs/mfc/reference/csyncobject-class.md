---
description: 'En savoir plus sur : classe CSyncObject'
title: CSyncObject, classe
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: 5743f632f9a8c482ac15995e8d2429851ba015d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318596"
---
# <a name="csyncobject-class"></a>CSyncObject, classe

Classe virtuelle pure qui fournit une fonctionnalité commune aux objets de synchronisation dans Win32.

## <a name="syntax"></a>Syntaxe

```
class CSyncObject : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|Construit un objet `CSyncObject`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSyncObject :: Lock](#lock)|Obtient l’accès à l’objet de synchronisation.|
|[CSyncObject :: Unlock](#unlock)|Obtient l’accès à l’objet de synchronisation.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[HANDLE CSyncObject :: Operator](#operator_handle)|Permet d’accéder à l’objet de synchronisation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSyncObject :: m_hObject](#m_hobject)|Handle de l’objet de synchronisation sous-jacent.|

## <a name="remarks"></a>Notes

Le bibliothèque MFC (Microsoft Foundation Class) fournit plusieurs classes dérivées de `CSyncObject` . Il s’agit de [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)et [CSemaphore](../../mfc/reference/csemaphore-class.md).

Pour plus d’informations sur l’utilisation des objets de synchronisation, consultez l’article [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmt. h

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a> CSyncObject::CSyncObject

Construit un objet de synchronisation avec le nom fourni.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Paramètres

*pstrName*<br/>
Nom de l'objet. Si la valeur est NULL, *pstrName* a la valeur null.

## <a name="csyncobjectlock"></a><a name="lock"></a> CSyncObject :: Lock

Appelez cette fonction pour accéder à la ressource contrôlée par l’objet de synchronisation.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Paramètres

*dwTimeout*<br/>
Spécifie la durée, en millisecondes, à attendre que l’objet de synchronisation soit disponible (signalé). S’il est infini, `Lock` attend que l’objet soit signalé avant de retourner.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Si l’objet de synchronisation est signalé, `Lock` retourne avec succès et le thread est propriétaire de l’objet. Si l’objet de synchronisation est non signalé (non disponible), `Lock` attend que l’objet de synchronisation soit signalé jusqu’au nombre de millisecondes spécifié dans le paramètre *dwTimeOut* . Si l’objet de synchronisation n’a pas été signalé dans le laps de temps spécifié, `Lock` retourne une erreur.

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a> CSyncObject :: m_hObject

Handle de l’objet de synchronisation sous-jacent.

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a> HANDLE CSyncObject :: Operator

Utilisez cet opérateur pour récupérer le handle de l' `CSyncObject` objet.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, le handle de l’objet de synchronisation ; Sinon, NULL.

### <a name="remarks"></a>Notes

Vous pouvez utiliser le handle pour appeler des API Windows directement.

## <a name="csyncobjectunlock"></a><a name="unlock"></a> CSyncObject :: Unlock

La déclaration de sans `Unlock` paramètres est une fonction virtuelle pure et doit être substituée par toutes les classes qui dérivent de `CSyncObject` .

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Paramètres

*lCount*<br/>
Non utilisé par l’implémentation par défaut.

*lpPrevCount*<br/>
Non utilisé par l’implémentation par défaut.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

L’implémentation par défaut de la déclaration avec deux paramètres retourne toujours la valeur TRUE. Cette fonction est appelée pour libérer l’accès à l’objet de synchronisation détenu par le thread appelant. La deuxième déclaration est fournie pour les objets de synchronisation tels que les sémaphores qui autorisent plus d’un accès à une ressource contrôlée.

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
