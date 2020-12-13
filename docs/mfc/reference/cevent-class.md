---
description: 'En savoir plus sur : CEvent, classe'
title: CEvent, classe
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: 0db33c89b52c3c6cb3dbf37cb3ea3da96e6c6c71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184696"
---
# <a name="cevent-class"></a>CEvent, classe

Représente un événement, qui est un objet de synchronisation qui permet à un thread de notifier à un autre thread qu’un événement s’est produit.

## <a name="syntax"></a>Syntaxe

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CEvent :: CEvent](#cevent)|Construit un objet `CEvent`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CEvent ::P ulseEvent](#pulseevent)|Définit l’événement comme étant disponible (signalé), libère les threads en attente et définit l’événement comme étant non disponible (non signalé).|
|[CEvent :: ResetEvent](#resetevent)|Définit l’événement comme étant non disponible (non signalé).|
|[CEvent :: SetEvent](#setevent)|Définit l’événement comme étant disponible (signalé) et libère tous les threads en attente.|
|[CEvent :: Unlock](#unlock)|Libère l’objet d’événement.|

## <a name="remarks"></a>Notes

Les événements sont utiles quand un thread doit savoir quand exécuter sa tâche. Par exemple, un thread qui copie des données vers une archive de données doit être averti quand de nouvelles données sont disponibles. En utilisant un `CEvent` objet pour notifier le thread de copie quand de nouvelles données sont disponibles, le thread peut effectuer sa tâche le plus rapidement possible.

`CEvent` les objets ont deux types : manuel et automatique.

Un `CEvent` objet automatique revient automatiquement à un État non signalé (non disponible) après la libération d’au moins un thread. Par défaut, un `CEvent` objet est automatique, sauf si vous transmettez `TRUE` le paramètre *bManualReset* pendant la construction.

Un `CEvent` objet manuel reste dans l’état défini par [SetEvent](#setevent) ou [ResetEvent](#resetevent) jusqu’à ce que l’autre fonction soit appelée. Pour créer un `CEvent` objet manuel, transmettez `TRUE` le `bManualReset` paramètre pendant la construction.

Pour utiliser un `CEvent` objet, construisez l' `CEvent` objet lorsqu’il est requis. Spécifiez le nom de l’événement que vous souhaitez attendre et spécifiez également que votre application doit être initialement propriétaire. Vous pouvez ensuite accéder à l’événement lorsque le constructeur retourne. Appelez [SetEvent](#setevent) pour signaler (rendre disponible) l’objet d’événement, puis appelez [Unlock](#unlock) lorsque vous avez terminé d’accéder à la ressource contrôlée.

Une autre méthode pour l’utilisation d' `CEvent` objets consiste à ajouter une variable de type `CEvent` en tant que membre de données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlé, appelez le constructeur du `CEvent` membre de données et spécifiez si l’événement est signalé initialement, ainsi que le type d’objet d’événement souhaité, le nom de l’événement (s’il sera utilisé au-delà des limites de processus) et tous les attributs de sécurité souhaités.

Pour accéder à une ressource contrôlée par un `CEvent` objet de cette manière, commencez par créer une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou tapez [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la méthode d’accès de votre ressource. Appelez ensuite la `Lock` méthode de l’objet Lock (par exemple, [CMultiLock :: Lock](../../mfc/reference/cmultilock-class.md#lock)). À ce stade, votre thread peut accéder à la ressource, attendre que la ressource soit libérée et y accéder, ou attendre que la ressource soit libérée, expirer et ne parvienne pas à accéder à la ressource. Dans tous les cas, votre ressource est accessible de manière thread-safe. Pour libérer la ressource, appelez `SetEvent` pour signaler l’objet d’événement, puis utilisez la `Unlock` méthode de l’objet de verrouillage (par exemple, [CMultiLock :: Unlock](../../mfc/reference/cmultilock-class.md#unlock)) ou laissez l’objet de verrou en dehors de l’étendue.

Pour plus d’informations sur l’utilisation des `CEvent` objets, consultez [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmt. h

## <a name="ceventcevent"></a><a name="cevent"></a> CEvent :: CEvent

Construit un objet nommé ou sans nom `CEvent` .

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Paramètres

*bInitiallyOwn*<br/>
Si la valeur est TRUE, le thread de l' `CMultilock` `CSingleLock` objet ou est activé. Dans le cas contraire, tous les threads souhaitant accéder à la ressource doivent attendre.

*bManualReset*<br/>
Si la valeur est TRUE, spécifie que l’objet d’événement est un événement manuel, sinon l’objet d’événement est un événement automatique.

*lpszName*<br/>
Nom de l'objet `CEvent`. Doit être fourni si l’objet sera utilisé au-delà des limites du processus. Si le nom correspond à un événement existant, le constructeur génère un nouvel `CEvent` objet qui fait référence à l’événement de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un événement, la construction échoue. Si la valeur est NULL, le nom a la valeur null.

*lpsaAttribute*<br/>
Attributs de sécurité pour l’objet d’événement. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) dans le SDK Windows.

### <a name="remarks"></a>Notes

Pour accéder ou libérer un `CEvent` objet, créez un objet [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) et appelez ses fonctions membres [Lock](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) .

Pour modifier l’état d’un `CEvent` objet à signalé (les threads n’ont pas besoin d’attendre), appelez [SetEvent](#setevent) ou [PulseEvent n'](#pulseevent). Pour définir l’état d’un `CEvent` objet sur non signalé (les threads doivent attendre), appelez [ResetEvent](#resetevent).

> [!IMPORTANT]
> Après avoir créé l' `CEvent` objet, utilisez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour vous assurer que le mutex n’existait pas déjà. Si le mutex s’est exécuté de façon inattendue, cela peut indiquer qu’un processus non autorisé est une opération d’occupation et peut être l’intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure recommandée pour la sécurité consiste à fermer le descripteur et à continuer comme en cas de défaillance lors de la création de l’objet.

## <a name="ceventpulseevent"></a><a name="pulseevent"></a> CEvent ::P ulseEvent

Définit l’état de l’événement comme étant signalé (disponible), libère tous les threads en attente et le réinitialise à l’état non signalé (non disponible) automatiquement.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Si l’événement est manuel, tous les threads en attente sont libérés, l’événement est défini sur non signalé et `PulseEvent` retourne. Si l’événement est automatique, un seul thread est libéré, l’événement est défini sur non signalé et `PulseEvent` retourne.

Si aucun thread n’est en attente, ou si aucun thread ne peut être libéré immédiatement, `PulseEvent` définit l’état de l’événement comme étant non signalé et retourne.

`PulseEvent` utilise la fonction Win32 sous-jacente `PulseEvent` , qui peut être momentanément supprimée de l’état d’attente par un appel de procédure asynchrone en mode noyau. Par conséquent, `PulseEvent` n’est pas fiable et ne doit pas être utilisé par les nouvelles applications. Pour plus d’informations, consultez la [fonction PulseEvent n'](/windows/win32/api/winbase/nf-winbase-pulseevent).

## <a name="ceventresetevent"></a><a name="resetevent"></a> CEvent :: ResetEvent

Définit l’état de l’événement comme étant non signalé jusqu’à ce qu’il soit explicitement défini comme signalé par la fonction membre [SetEvent](#setevent) .

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Cela entraîne l’attente de tous les threads qui souhaitent accéder à cet événement.

Cette fonction membre n’est pas utilisée par les événements automatiques.

## <a name="ceventsetevent"></a><a name="setevent"></a> CEvent :: SetEvent

Définit l’état de l’événement comme étant signalé, en libérant tous les threads en attente.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si la fonction a réussi ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’événement est manuel, l’événement reste signalé jusqu’à ce que [ResetEvent](#resetevent) soit appelé. Dans ce cas, plusieurs threads peuvent être libérés. Si l’événement est automatique, l’événement reste signalé jusqu’à ce qu’un seul thread soit libéré. Le système définit alors l’état de l’événement comme étant non signalé. Si aucun thread n’attend, l’état reste signalé jusqu’à ce qu’un thread soit libéré.

## <a name="ceventunlock"></a><a name="unlock"></a> CEvent :: Unlock

Libère l’objet d’événement.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le thread appartient à l’objet d’événement et que l’événement est un événement automatique ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par les threads qui possèdent actuellement un événement automatique pour le libérer une fois qu’ils ont été effectués, si leur objet de verrouillage doit être réutilisé. Si l’objet Lock ne doit pas être réutilisé, cette fonction sera appelée par le destructeur de l’objet Lock.

## <a name="see-also"></a>Voir aussi

[CSyncObject, classe](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
