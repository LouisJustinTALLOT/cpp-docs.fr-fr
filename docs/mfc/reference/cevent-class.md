---
title: CEvent, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8dff47314c5e8932a6f5a2a2078fd70a86c9229b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386494"
---
# <a name="cevent-class"></a>CEvent, classe

Représente un événement, qui est un objet de synchronisation qui permet à un thread de notifier à un autre un événement s’est produite.

## <a name="syntax"></a>Syntaxe

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|Construit un objet `CEvent`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|Définit l’événement à disponibles (signalé), libère les threads en attente et définit l’événement comme non disponible ("non signalé").|
|[CEvent::ResetEvent](#resetevent)|Définit l’événement comme non disponible ("non signalé").|
|[CEvent::SetEvent](#setevent)|Affecte à l’événement disponible (signalé) et libère tous les threads en attente.|
|[CEvent::Unlock](#unlock)|Libère l’objet d’événement.|

## <a name="remarks"></a>Notes

Les événements sont utiles lorsqu’un thread doit savoir à quel moment effectuer sa tâche. Par exemple, un thread qui copie les données vers une archive de données doit être averti lorsque de nouvelles données sont disponibles. En utilisant un `CEvent` objet de notifier le thread de copie lorsque de nouvelles données sont disponibles, le thread peut réaliser sa tâche dès que possible.

`CEvent` les objets ont deux types : automatique et manuel.

Automatique `CEvent` objet retourne automatiquement à un état non signalé de (non disponible) après la publication d’au moins un thread. Par défaut, un `CEvent` objet est automatique, sauf si vous transmettez `TRUE` pour le *bManualReset* paramètre pendant la construction.

Un manuel `CEvent` objet reste dans l’état défini [SetEvent](#setevent) ou [ResetEvent](#resetevent) jusqu'à ce que l’autre fonction est appelée. Pour créer un manuel `CEvent` d’objet, passer `TRUE` pour le `bManualReset` paramètre pendant la construction.

Pour utiliser un `CEvent` d’objet, construire le `CEvent` objet lorsqu’il est requis. Spécifiez le nom de l’événement que vous souhaitez attendre et également spécifier que votre application doit initialement êtes bien le propriétaire. Vous pouvez ensuite accéder à l’événement lorsque le constructeur retourne. Appelez [SetEvent](#setevent) au signal (disposition) l’objet d’événement et puis appelez [Unlock](#unlock) lorsque vous avez terminé l’accès à la ressource contrôlée.

Une autre méthode pour l’utilisation de `CEvent` objets consiste à ajouter une variable de type `CEvent` comme membre de données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlée, appelez le constructeur de la `CEvent` membre de données et spécifiez si l’événement est signalé initialement, ainsi que specifythe type d’objet d’événement souhaité, le nom de l’événement (si elle sera utilisée entre les processus limites) et des attributs de sécurité souhaité.

Pour accéder à une ressource contrôlée par un `CEvent` de l’objet de cette manière, commencez par créer une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou type [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la méthode d’accès de votre ressource. Appelez ensuite la `Lock` méthode de l’objet de verrouillage (par exemple, [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). À ce stade, votre thread sera soit accéder à la ressource, l’attente de la ressource à libérée et y accéder ou attendez que la ressource doit être publié, le délai d’expiration et ne parviennent pas à accéder à la ressource. Dans tous les cas, votre ressource a accédé de manière thread-safe. Pour libérer la ressource, appelez `SetEvent` pour signaler l’objet d’événement, puis utiliser le `Unlock` méthode de l’objet de verrouillage (par exemple, [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), ou laisser l’objet de verrouillage se situent hors de portée.

Pour plus d’informations sur l’utilisation `CEvent` , consultez [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxmt.h

##  <a name="cevent"></a>  CEvent::CEvent

Construit un nommé ou sans nom `CEvent` objet.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Paramètres

*bInitiallyOwn*<br/>
Si la valeur est TRUE, le thread pour le `CMultilock` ou `CSingleLock` objet est activé. Sinon, tous les threads qui veulent accéder à la ressource doivent attendre.

*bManualReset*<br/>
Si la valeur est TRUE, spécifie que l’objet d’événement est un événement manuel, sinon l’objet d’événement est un événement automatique.

*Caractère*<br/>
Nom de l'objet `CEvent`. Doit être fourni si l’objet doit être utilisé au-delà des limites de processus. Si le nom correspond à un événement existant, le constructeur crée quand même un `CEvent` objet qui fait référence à l’événement de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un événement, la construction échoue. Si NULL, le nom sera null.

*lpsaAttribute*<br/>
Attributs de sécurité de l’objet d’événement. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) dans le SDK Windows.

### <a name="remarks"></a>Notes

Pour accéder à ou libérer un `CEvent` d’objet, de créer un [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) objet et appelez ses [verrou](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) fonctions membres.

Pour modifier l’état d’un `CEvent` objet signalé (threads n’ont pas d’attente), appelez [SetEvent](#setevent) ou [PulseEvent](#pulseevent). Pour définir l’état d’un `CEvent` objet comme étant non signalé (threads doivent attendre), appelez [ResetEvent](#resetevent).

> [!IMPORTANT]
>  Après avoir créé le `CEvent` de l’objet, utilisez [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) pour vous assurer que le mutex n’existe pas déjà. Si le mutex n’existait inattendu, cela peut indiquer un processus non fiable est l’occupation et peut être ayant l’intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure en termes de sécurité recommandée consiste à fermer le handle et continuer comme si une défaillance s’est produite lors de la création de l’objet.

##  <a name="pulseevent"></a>  CEvent::PulseEvent

Définit l’état de l’événement signalé (disponible), libère tous les threads en attente et une remise à "non signalé" (non disponible) automatiquement.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; sinon 0.

### <a name="remarks"></a>Notes

Si l’événement est manuel, tous les threads en attente sont publiées, l’événement est défini à "non signalé", et `PulseEvent` retourne. Si l’événement est automatique, un seul thread est libéré, l’événement est défini à "non signalé", et `PulseEvent` retourne.

Si aucun thread n’attend, ou si aucun thread ne peut être libéré immédiatement, `PulseEvent` définit l’état de l’événement à "non signalé" et le retourne.

`PulseEvent` utilise Win32 sous-jacente `PulseEvent` (fonction), qui peut être momentanément supprimée à partir de l’état d’attente par un appel de procédure asynchrone en mode noyau. Par conséquent, `PulseEvent` n’est pas fiable et ne doit pas être utilisé par les nouvelles applications. Pour plus d’informations, consultez le [PulseEvent fonction](/windows/desktop/api/winbase/nf-winbase-pulseevent).

##  <a name="resetevent"></a>  CEvent::ResetEvent

Définit l’état de l’événement à "non signalé" jusqu'à ce que le définir explicitement à signalé par le [SetEvent](#setevent) fonction membre.

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; sinon 0.

### <a name="remarks"></a>Notes

Par conséquent, tous les threads qui souhaitent accéder à cet événement d’attente.

Cette fonction membre n’est pas utilisée par les événements automatiques.

##  <a name="setevent"></a>  CEvent::SetEvent

Définit l’état de l’événement signalé, libérer les threads en attente.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi, sinon, 0.

### <a name="remarks"></a>Notes

Si l’événement est manuelle, l’événement reste signalé jusqu'à ce que [ResetEvent](#resetevent) est appelée. Plusieurs threads peuvent être lancées dans ce cas. Si l’événement est automatique, l’événement reste signalé jusqu'à ce qu’un seul thread est libéré. Le système définit ensuite l’état de l’événement à "non signalé". Si aucun thread n’attend, l’état reste signalé jusqu'à ce qu’un seul thread est libéré.

##  <a name="unlock"></a>  CEvent::Unlock

Libère l’objet d’événement.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le thread qui possède l’objet d’événement et l’événement est un événement automatique ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par les threads qui possèdent actuellement un événement automatique pour libérer une fois qu’elles sont faites, si leur objet verrou doit être réutilisé. Si l’objet de verrouillage n’est ne pas à être réutilisé, cette fonction est appelée par le destructeur de l’objet de verrouillage.

## <a name="see-also"></a>Voir aussi

[CSyncObject, classe](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

