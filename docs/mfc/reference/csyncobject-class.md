---
title: CSyncObject, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91a3978b83be0cc1bc85d57cbde87d17eb4cc6d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082799"
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
|[CSyncObject::Lock](#lock)|Accède à l’objet de synchronisation.|
|[CSyncObject::Unlock](#unlock)|Accède à l’objet de synchronisation.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSyncObject::operator HANDLE](#operator_handle)|Fournit l’accès à l’objet de synchronisation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|Le handle vers l’objet sous-jacent de la synchronisation.|

## <a name="remarks"></a>Notes

La bibliothèque Microsoft Foundation Class fournit plusieurs classes dérivées de `CSyncObject`. Il s’agit de [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), et [CSemaphore](../../mfc/reference/csemaphore-class.md).

Pour plus d’informations sur la façon d’utiliser les objets de synchronisation, consultez l’article [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxmt.h

##  <a name="csyncobject"></a>  CSyncObject::CSyncObject

Construit un objet de synchronisation avec le nom fourni.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Paramètres

*pstrName*<br/>
Nom de l'objet. Si NULL, *pstrName* sera null.

##  <a name="lock"></a>  CSyncObject::Lock

Appelez cette fonction pour accéder à la ressource contrôlée par l’objet de synchronisation.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Paramètres

*dwTimeout*<br/>
Spécifie la quantité de temps en millisecondes à attendre pour l’objet de synchronisation soit disponible (signalé). Si elle est infinie, `Lock` attendra jusqu'à ce que l’objet est signalé avant de retourner.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; sinon 0.

### <a name="remarks"></a>Notes

Si l’objet de synchronisation est signalé, `Lock` renvoie correctement et que le thread possède maintenant l’objet. Si l’objet de synchronisation est "non signalé" (non disponible), `Lock` attendra pour l’objet de synchronisation soit signalé jusqu’au nombre de millisecondes spécifié dans le *dwTimeOut* paramètre. Si l’objet de synchronisation ne pas signalé dans le laps de temps, `Lock` échoue.

##  <a name="m_hobject"></a>  CSyncObject::m_hObject

Le handle vers l’objet sous-jacent de la synchronisation.

```
HANDLE m_hObject;
```

##  <a name="operator_handle"></a>  CSyncObject::operator HANDLE

Utilisez cet opérateur pour obtenir le handle de la `CSyncObject` objet.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, le handle de l’objet de synchronisation ; Sinon, NULL.

### <a name="remarks"></a>Notes

Vous pouvez utiliser le handle d’appeler directement les API de Windows.

##  <a name="unlock"></a>  CSyncObject::Unlock

La déclaration de `Unlock` sans paramètres est une fonction virtuelle pure et doit être substitué par toutes les classes dérivant de `CSyncObject`.

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

### <a name="return-value"></a>Valeur de retour

Par défaut implémentation retourne toujours TRUE.

### <a name="remarks"></a>Notes

L’implémentation par défaut de la déclaration avec deux paramètres toujours retourne la valeur TRUE. Cette fonction est appelée pour libérer l’accès à l’objet de synchronisation détenu par le thread appelant. La seconde déclaration est fournie pour les objets de synchronisation tels que les sémaphores qui autorisent l’accès de plusieurs d’une ressource contrôlée.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

