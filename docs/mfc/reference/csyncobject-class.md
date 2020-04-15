---
title: Classe CSyncObject
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
ms.openlocfilehash: ebfbc185cdca2effc96ce2e6d96d05f997c52bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365968"
---
# <a name="csyncobject-class"></a>Classe CSyncObject

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
|[CSyncObject::Lock](#lock)|L’accès à l’objet de synchronisation a accès à l’objet de synchronisation.|
|[CSyncObject::Unlock](#unlock)|L’accès à l’objet de synchronisation a accès à l’objet de synchronisation.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSyncObject::opérateur HANDLE](#operator_handle)|Donne accès à l’objet de synchronisation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|La poignée de l’objet de synchronisation sous-jacent.|

## <a name="remarks"></a>Notes

La Bibliothèque de classe microsoft `CSyncObject`Foundation offre plusieurs classes dérivées de . Ce sont [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), et [CSemaphore](../../mfc/reference/csemaphore-class.md).

Pour plus d’informations sur l’utilisation des objets de synchronisation, consultez l’article [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmt.h

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSyncObject::CSyncObject

Construit un objet de synchronisation avec le nom fourni.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Paramètres

*pstrName (en)*<br/>
Nom de l'objet. Si NULL, *pstrName* sera nul.

## <a name="csyncobjectlock"></a><a name="lock"></a>CSyncObject::Lock

Appelez cette fonction pour accéder à la ressource contrôlée par l’objet de synchronisation.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Paramètres

*dwTimeout*<br/>
Spécifie le temps en millisecondes pour attendre que l’objet de synchronisation soit disponible (signalé). Si INFINITE, `Lock` attendra que l’objet soit signalé avant de revenir.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Si l’objet de synchronisation `Lock` est signalé, reviendra avec succès et le thread possède maintenant l’objet. Si l’objet de synchronisation n’est pas `Lock` signé (indisponible), attendra que l’objet de synchronisation soit signalé jusqu’au nombre de millisecondes spécifiées dans le paramètre *dwTimeOut.* Si l’objet de synchronisation n’est pas signalé `Lock` dans le laps de temps spécifié, l’échec des retours.

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a>CSyncObject::m_hObject

La poignée de l’objet de synchronisation sous-jacent.

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a>CSyncObject::opérateur HANDLE

Utilisez cet opérateur pour obtenir `CSyncObject` la poignée de l’objet.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, la poignée de l’objet de synchronisation; autrement, NULL.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la poignée pour appeler directement les API Windows.

## <a name="csyncobjectunlock"></a><a name="unlock"></a>CSyncObject::Unlock

La déclaration `Unlock` de sans paramètres est une fonction virtuelle pure, et doit être `CSyncObject`remplacé par toutes les classes dérivées de .

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Paramètres

*lCompte*<br/>
Non utilisé par implémentation par défaut.

*lpPrevCompte*<br/>
Non utilisé par implémentation par défaut.

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut renvoie toujours TRUE.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de la déclaration avec deux paramètres renvoie toujours VRAI. Cette fonction est appelée pour libérer l’accès à l’objet de synchronisation appartenant au fil d’appel. La deuxième déclaration est prévue pour les objets de synchronisation tels que les sémaphores qui permettent à plus d’un accès à une ressource contrôlée.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
