---
title: COleMessageFilter, classe
ms.date: 11/04/2016
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
ms.openlocfilehash: f6db5f012aedf08edd87980e304e181295bfb953
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374924"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter, classe

Gère l'accès concurrentiel requis par l'interaction des applications OLE.

## <a name="syntax"></a>Syntaxe

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|Construit un objet `COleMessageFilter`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Met l’application dans l’état occupé.|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Permet et désactive la boîte de dialogue qui apparaît lorsqu’une application appelée est occupée.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Permet et désactive la boîte de dialogue qui apparaît lorsqu’une application appelée ne répond pas.|
|[COleMessageFilter::EndBusyState](#endbusystate)|Résilie l’état occupé de l’application.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Appelé par le cadre pour traiter les messages pendant qu’un appel OLE est en cours.|
|[COleMessageFilter::Enregistrement](#register)|Enregistre le filtre de message avec les DLLs du système OLE.|
|[COleMessageFilter::Revoke](#revoke)|Révoque l’enregistrement du filtre de message avec le système OLE DLLs.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Détermine la réponse de l’application occupée à un appel OLE.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Détermine combien de temps l’application attend une réponse à un appel OLE.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|Détermine la réponse de l’application d’appel à une demande occupée.|

## <a name="remarks"></a>Notes

La `COleMessageFilter` classe est utile dans les applications de serveur d’édition visuelle et de conteneurs, ainsi que les applications d’automatisation OLE. Pour les applications serveur qui sont appelées, cette classe peut être utilisée pour rendre l’application «occupée» de sorte que les appels entrants à partir d’autres applications de conteneurs sont soit annulés ou rejugés plus tard. Ce groupe peut également être utilisé pour déterminer les mesures à prendre par une demande d’appel lorsque l’application appelée est occupée.

L’utilisation courante est pour une application de serveur d’appeler [BeginBusyState](#beginbusystate) et [EndBusyState](#endbusystate) quand il serait dangereux pour un document ou un autre objet accessible OLE d’être détruit. Ces appels sont effectués dans [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) pendant les mises à jour utilisateur-interface.

Par défaut, `COleMessageFilter` un objet est attribué lorsque l’application est parascée. Il peut être récupéré avec [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

Il s’agit d’une classe avancée; vous avez rarement besoin de travailler avec elle directement.

Pour plus d’informations, voir l’article [Serveurs: Implémenter un serveur](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a>COleMessageFilter::BeginBusyState

Appelez cette fonction pour commencer un état occupé.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Notes

Il fonctionne en collaboration avec [EndBusyState](#endbusystate) pour contrôler l’état occupé de l’application. La fonction [SetBusyPoreply](#setbusyreply) détermine la réponse de l’application à l’appel des applications lorsqu’elle est occupée.

L’incrément `BeginBusyState` et `EndBusyState` l’augmentation des appels, respectivement, un compteur qui détermine si l’application est occupée. Par exemple, deux `BeginBusyState` appels à `EndBusyState` et un appel pour encore aboutir à un état occupé. Pour annuler un état occupé, `EndBusyState` il est `BeginBusyState` nécessaire d’appeler le même nombre de fois a été appelé.

Par défaut, le cadre entre dans l’état occupé pendant le traitement au ralenti, qui est effectué par [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Pendant que l’application traite ON_COMMANDUPDATEUI notifications, les appels entrants sont traités plus tard, une fois le traitement inactif terminé.

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter

Crée un objet `COleMessageFilter` .

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog

Permet et désactive la boîte de dialogue occupée, qui est affichée lorsque le délai en attente de message expire (voir [SetRetryReply](#setretryreply)) lors d’un appel OLE.

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnableBusy (en)*<br/>
Précise si la boîte de dialogue « occupée » est activée ou désactivée.

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog

Permet et désactive la boîte de dialogue « ne pas répondre », qui s’affiche si un message clavier ou souris est en attente lors d’un appel OLE et que l’appel s’est interrompu.

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnableNotResponding*<br/>
Précise si la boîte de dialogue « ne pas répondre » est activée ou désactivée.

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a>COleMessageFilter::EndBusyState

Appelez cette fonction pour mettre fin à un état occupé.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Notes

Il fonctionne en collaboration avec [BeginBusyState](#beginbusystate) pour contrôler l’état occupé de l’application. La fonction [SetBusyPoreply](#setbusyreply) détermine la réponse de l’application à l’appel des applications lorsqu’elle est occupée.

L’incrément `BeginBusyState` et `EndBusyState` l’augmentation des appels, respectivement, un compteur qui détermine si l’application est occupée. Par exemple, deux `BeginBusyState` appels à `EndBusyState` et un appel pour encore aboutir à un état occupé. Pour annuler un état occupé, `EndBusyState` il est `BeginBusyState` nécessaire d’appeler le même nombre de fois a été appelé.

Par défaut, le cadre entre dans l’état occupé pendant le traitement au ralenti, qui est effectué par [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Pendant que l’application traite ON_UPDATE_COMMAND_UI notifications, les appels entrants sont traités après la fin du traitement au ralenti.

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a>COleMessageFilter::OnMessagePending

Appelé par le cadre pour traiter les messages pendant qu’un appel OLE est en cours.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Pointeur vers le message en attente.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Lorsqu’une demande d’appel attend qu’un `OnMessagePending` appel soit effectué, le cadre passe par un pointeur vers le message en attente. Par défaut, le cadre envoie WM_PAINT messages, de sorte que les mises à jour de fenêtre peuvent se produire au cours d’un appel qui prend beaucoup de temps.

Vous devez enregistrer votre filtre de message au moyen d’un appel à [s’inscrire](#register) avant qu’il puisse devenir actif.

## <a name="colemessagefilterregister"></a><a name="register"></a>COleMessageFilter::Enregistrement

Enregistre le filtre de message avec les DLLs du système OLE.

```
BOOL Register();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un filtre de message n’a aucun effet à moins qu’il ne soit enregistré auprès des DLL système. Habituellement, le code d’initialisation de votre application enregistre le filtre de message de l’application. Tout autre filtre de message enregistré par votre demande doit être révoqué avant la fin du programme par un appel à [révoquer](#revoke).

Le filtre de message par défaut du cadre est automatiquement enregistré lors de l’initialisation et révoqué à la fin.

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a>COleMessageFilter::Revoke

Révoque une inscription précédente effectuée par un appel à [l’inscription](#register).

```
void Revoke();
```

### <a name="remarks"></a>Notes

Un filtre de message doit être révoqué avant la fin du programme.

Le filtre de message par défaut, qui est créé et enregistré automatiquement par le cadre, est également automatiquement révoqué.

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a>COleMessageFilter::SetBusyReply

Cette fonction définit la « réponse occupée » de l’application.

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>Paramètres

*nBusyPorétre*<br/>
Une valeur `SERVERCALL` de l’énumération, qui est définie dans COMPOBJ. H. Il peut avoir l’une des valeurs suivantes:

- SERVERCALL_ISHANDLED La demande peut accepter des appels, mais peut échouer dans le traitement d’un appel particulier.

- SERVERCALL_REJECTED L’application ne sera probablement jamais en mesure de traiter un appel.

- SERVERCALL_RETRYLATER La demande est temporairement dans un état dans lequel elle ne peut pas traiter un appel.

### <a name="remarks"></a>Notes

Les fonctions [BeginBusyState](#beginbusystate) et [EndBusyState](#endbusystate) contrôlent l’état occupé de l’application.

Lorsqu’une application a été prise `BeginBusyState`avec un appel à , il répond aux appels du système `SetBusyReply`OLE DLLs avec une valeur déterminée par le dernier paramètre de . L’application d’appel utilise cette réponse occupée pour déterminer quelles mesures prendre.

Par défaut, la réponse occupée est SERVERCALL_RETRYLATER. Cette réponse provoque la demande d’appel de réessayer l’appel dès que possible.

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay

Détermine combien de temps la demande d’appel attend une réponse de la demande appelée avant de prendre d’autres mesures.

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>Paramètres

*nTimeout (en)*<br/>
Nombre de millisecondes pour le délai en attente de message.

### <a name="remarks"></a>Notes

Cette fonction fonctionne de concert avec [SetRetryReply](#setretryreply).

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a>COleMessageFilter::SetRetryReply

Détermine l’action de l’application d’appel lorsqu’elle reçoit une réponse occupée d’une demande appelée.

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>Paramètres

*nRetryPorérisme*<br/>
Nombre de millisecondes entre les retries.

### <a name="remarks"></a>Notes

Lorsqu’une application appelée indique qu’elle est occupée, l’application d’appel peut décider d’attendre que le serveur ne soit plus occupé, de réessayer immédiatement ou de réessayer après un intervalle spécifié. Il peut également décider d’annuler l’appel tout à fait.

La réponse de l’appelant est contrôlée `SetRetryReply` par les fonctions et [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply`détermine combien de temps l’application d’appel doit attendre entre les retries pour un appel donné. `SetMessagePendingDelay`détermine combien de temps l’application d’appel attend une réponse du serveur avant de prendre d’autres mesures.

Habituellement, les défauts sont acceptables et n’ont pas besoin d’être changés. Le cadre retries l’appel chaque *milliseconde nRetryReply* jusqu’à ce que l’appel passe ou le retard en attente de message a expiré. Une valeur de 0 pour *nRetryReply* spécifie une nouvelle tentative immédiate, et - 1 spécifie l’annulation de l’appel.

Lorsque le délai en attente de message a expiré, l’OLE "boîte de dialogue occupé" (voir [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) est affiché de sorte que l’utilisateur peut choisir d’annuler ou de rejuger l’appel. Appelez [EnableBusyDialog](#enablebusydialog) pour activer ou désactiver cette boîte de dialogue.

Lorsqu’un message clavier ou souris est en attente pendant un appel et que l’appel est annulé (dépassant le délai en attente de message), la boîte de dialogue « ne répondant pas » s’affiche. Appelez [EnableNotRespondingDialog](#enablenotrespondingdialog) pour activer ou désactiver cette boîte de dialogue. Habituellement, cet état de choses indique que quelque chose a mal tourné et l’utilisateur s’impatiente.

Lorsque les dialogues sont désactivés, la « réponse de réessaie » actuelle est toujours utilisée pour les appels à des applications occupées.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
