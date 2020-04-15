---
title: Classe CEvent
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
ms.openlocfilehash: 009a17342cb92025d67bf2fe0df1b9d5c7c0c6f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373957"
---
# <a name="cevent-class"></a>Classe CEvent

Représente un événement, qui est un objet de synchronisation qui permet à un thread d’en informer un autre qu’un événement s’est produit.

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
|[CEvent::PulseEvent](#pulseevent)|Définit l’événement à disposition (signalé), libère des fils d’attente et définit l’événement à l’indisponible (non-signé).|
|[CEvent::Resetevent](#resetevent)|Définit l’événement à l’indisponible (non-signé).|
|[CEvent::SetEvent](#setevent)|Définit l’événement à disposition (signalé) et libère tous les threads d’attente.|
|[CEvent::Unlock](#unlock)|Libère l’objet de l’événement.|

## <a name="remarks"></a>Notes

Les événements sont utiles lorsqu’un thread doit savoir quand effectuer sa tâche. Par exemple, un thread qui copie les données à une archive de données doit être notifié lorsque de nouvelles données sont disponibles. En utilisant `CEvent` un objet pour aviser le fil de copie lorsque de nouvelles données sont disponibles, le thread peut effectuer sa tâche dès que possible.

`CEvent`objets ont deux types: manuel et automatique.

Un `CEvent` objet automatique retourne automatiquement à un état non signalé (indisponible) après la sortie d’au moins un thread. Par défaut, `CEvent` un objet est `TRUE` automatique à moins que vous ne passiez pour le paramètre *bManualReset* pendant la construction.

Un `CEvent` objet manuel reste dans l’état défini par [SetEvent](#setevent) ou [ResetEvent](#resetevent) jusqu’à ce que l’autre fonction soit appelée. Pour créer `CEvent` un objet `TRUE` manuel, `bManualReset` passez pour le paramètre pendant la construction.

Pour utiliser `CEvent` un objet, construisez l’objet `CEvent` quand il est nécessaire. Spécifiez le nom de l’événement que vous souhaitez attendre, et précisez également que votre application doit d’abord en être propriétaire. Vous pouvez ensuite accéder à l’événement lorsque le constructeur revient. Appelez [SetEvent](#setevent) pour signaler (mettre à disposition) l’objet de l’événement, puis appeler [Déverrouiller](#unlock) lorsque vous avez terminé d’accéder à la ressource contrôlée.

Une autre méthode `CEvent` pour l’utilisation d’objets est d’ajouter une variable de type `CEvent` en tant que membre de données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlé, `CEvent` appelez le constructeur du membre de données et spécifier si l’événement est initialement signalé, et spécifiez également le type d’objet d’événement que vous voulez, le nom de l’événement (s’il sera utilisé au-delà des limites du processus), et tous les attributs de sécurité que vous voulez.

Pour accéder à une `CEvent` ressource contrôlée par un objet de cette manière, créez d’abord une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou de type [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la méthode d’accès de votre ressource. Ensuite, `Lock` appelez la méthode de l’objet de verrouillage (par exemple, [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). À ce stade, votre thread aura soit accès à la ressource, attendre que la ressource soit libérée et y accéder, soit attendre que la ressource soit libérée, qu’elle n’ait pas accès à la ressource et qu’elle n’ait pas accès à la ressource. Dans tous les cas, votre ressource a été consultée d’une manière sans fil. Pour libérer la `SetEvent` ressource, appelez pour signaler l’objet de l’événement, puis utilisez la `Unlock` méthode de l’objet de verrouillage (par exemple, [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), ou laissez l’objet de verrouillage tomber hors de portée.

Pour plus d’informations `CEvent` sur la façon d’utiliser des objets, voir [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmt.h

## <a name="ceventcevent"></a><a name="cevent"></a>CEvent::CEvent

Construit un objet nommé `CEvent` ou anonyme.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Paramètres

*bInitiallyOwn (en anglais)*<br/>
Si VRAI, le `CMultilock` fil `CSingleLock` pour ou l’objet est activé. Sinon, tous les threads qui veulent accéder à la ressource doivent attendre.

*bManualReset (en)*<br/>
Si VRAI, spécifie que l’objet de l’événement est un événement manuel, sinon l’objet de l’événement est un événement automatique.

*lpszName (en)*<br/>
Nom de l'objet `CEvent`. Doit être fourni si l’objet sera utilisé au-delà des limites du processus. Si le nom correspond à un événement existant, le constructeur construit un nouvel `CEvent` objet qui fait référence à l’événement de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un événement, la construction échouera. Si NULL, le nom sera nul.

*lpsaAttribute*<br/>
Attributs de sécurité pour l’objet de l’événement. Pour une description complète de cette structure, voir [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) dans le SDK Windows.

### <a name="remarks"></a>Notes

Pour accéder ou `CEvent` libérer un objet, créez un objet [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) et appelez ses fonctions de membre [Lock](../../mfc/reference/csinglelock-class.md#lock) and [Unlock.](../../mfc/reference/csinglelock-class.md#unlock)

Pour modifier l’état d’un `CEvent` objet à signalé (les fils n’ont pas à attendre), appelez [SetEvent](#setevent) ou [PulseEvent](#pulseevent). Pour définir l’état d’un `CEvent` objet à non-signé (les fils doivent attendre), appelez [ResetEvent](#resetevent).

> [!IMPORTANT]
> Après avoir `CEvent` créé l’objet, utilisez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour vous assurer que le mutex n’existe pas déjà. Si le mutex a existé de façon inattendue, il peut indiquer un processus voyous est accroupi et peut-être l’intention d’utiliser le mutex malicieusement. Dans ce cas, la procédure recommandée de sécurité est de fermer la poignée et de continuer comme s’il y avait un échec dans la création de l’objet.

## <a name="ceventpulseevent"></a><a name="pulseevent"></a>CEvent::PulseEvent

Définit l’état de l’événement à signaler (disponible), libère tous les threads d’attente, et le réinitialise à nonsignaled (indisponible) automatiquement.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Si l’événement est manuel, tous les fils d’attente sont libérés, l’événement est réglé sur non-signé, et `PulseEvent` revient. Si l’événement est automatique, un seul thread est libéré, l’événement est réglé sur non-signé, et `PulseEvent` revient.

Si aucun thread n’est en attente, ou `PulseEvent` aucun thread ne peut être libéré immédiatement, définit l’état de l’événement à nonsignaled et revient.

`PulseEvent`utilise la `PulseEvent` fonction trumpante sous-jacente, qui peut être momentanément retirée de l’état d’attente par un appel de procédure asynchrone en mode noyau. Par `PulseEvent` conséquent, n’est pas fiable et ne doit pas être utilisé par de nouvelles applications. Pour plus d’informations, consultez la [fonction PulseEvent](/windows/win32/api/winbase/nf-winbase-pulseevent).

## <a name="ceventresetevent"></a><a name="resetevent"></a>CEvent::Resetevent

Définit l’état de l’événement à non-signé jusqu’à ce qu’il soit explicitement réglé par la fonction [membre SetEvent.](#setevent)

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Cela provoque tous les threads souhaitant accéder à cet événement d’attendre.

Cette fonction de membre n’est pas utilisée par des événements automatiques.

## <a name="ceventsetevent"></a><a name="setevent"></a>CEvent::SetEvent

Définit l’état de l’événement à signaler, libérant tous les fils d’attente.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie, sinon 0.

### <a name="remarks"></a>Notes

Si l’événement est manuel, l’événement restera signalé jusqu’à ce que [ResetEvent](#resetevent) soit appelé. Plus d’un thread peut être libéré dans ce cas. Si l’événement est automatique, l’événement restera signalé jusqu’à ce qu’un seul thread soit libéré. Le système définira ensuite l’état de l’événement à des non-insignes. Si aucun thread n’est en attente, l’état reste signalé jusqu’à ce qu’un thread soit libéré.

## <a name="ceventunlock"></a><a name="unlock"></a>CEvent::Unlock

Libère l’objet de l’événement.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le fil possédait l’objet de l’événement et l’événement est un événement automatique; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par des threads qui possèdent actuellement un événement automatique pour le libérer après qu’ils soient faits, si leur objet de verrouillage doit être réutilisé. Si l’objet de verrouillage ne doit pas être réutilisé, cette fonction sera appelée par le destructeur de l’objet de verrouillage.

## <a name="see-also"></a>Voir aussi

[Classe CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
