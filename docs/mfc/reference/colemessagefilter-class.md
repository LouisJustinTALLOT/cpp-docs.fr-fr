---
description: 'En savoir plus sur : classe COleMessageFilter'
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
ms.openlocfilehash: f0ab1d473704f5355933c04072a195c12fb71c73
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226894"
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
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Active et désactive la boîte de dialogue qui s’affiche lorsqu’une application appelée est occupée.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Active et désactive la boîte de dialogue qui s’affiche lorsqu’une application appelée ne répond pas.|
|[COleMessageFilter::EndBusyState](#endbusystate)|Met fin à l’état occupé de l’application.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Appelé par l’infrastructure pour traiter des messages pendant qu’un appel OLE est en cours.|
|[COleMessageFilter :: Register](#register)|Inscrit le filtre de messages avec les DLL système OLE.|
|[COleMessageFilter :: Revoke](#revoke)|Révoque l’inscription du filtre de messages avec les DLL système OLE.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Détermine la réponse de l’application occupée à un appel OLE.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Détermine la durée pendant laquelle l’application attend une réponse à un appel OLE.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|Détermine la réponse de l’application appelante à une application occupée.|

## <a name="remarks"></a>Notes

La `COleMessageFilter` classe est utile dans les applications serveur et conteneur d’édition visuelle, ainsi que dans les applications OLE Automation. Pour les applications serveur qui sont appelées, cette classe peut être utilisée pour que l’application soit « occupée » afin que les appels entrants d’autres applications de conteneur soient annulés ou retentés ultérieurement. Cette classe peut également être utilisée pour déterminer l’action à entreprendre par une application appelante lorsque l’application appelée est occupée.

L’utilisation courante consiste à faire en sorte qu’une application serveur appelle [BeginBusyState](#beginbusystate) et [EndBusyState](#endbusystate) lorsqu’il serait dangereux de détruire un document ou un autre objet OLE accessible. Ces appels sont effectués dans [CWinApp :: OnIdle](../../mfc/reference/cwinapp-class.md#onidle) lors des mises à jour de l’interface utilisateur.

Par défaut, un `COleMessageFilter` objet est alloué lorsque l’application est initialisée. Il peut être récupéré avec [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

Il s’agit d’une classe avancée. vous avez rarement besoin de l’utiliser directement.

Pour plus d’informations, consultez l’article [serveurs : implémentation d’un serveur](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a> COleMessageFilter::BeginBusyState

Appelez cette fonction pour démarrer un état occupé.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Notes

Il fonctionne conjointement avec [EndBusyState](#endbusystate) pour contrôler l’état de disponibilité de l’application. La fonction [SetBusyReply](#setbusyreply) détermine la réponse de l’application à l’appel d’applications lorsqu’elle est occupée.

`BeginBusyState`Et `EndBusyState` appelle l’incrémentation et la décrémentation, respectivement, un compteur qui détermine si l’application est occupée. Par exemple, deux appels à `BeginBusyState` et un appel à ont `EndBusyState` toujours pour résultat un état occupé. Pour annuler un état occupé, il est nécessaire d’appeler `EndBusyState` le même nombre de fois que l’appel de la méthode `BeginBusyState` .

Par défaut, le Framework passe à l’état occupé pendant le traitement de l’inactivité, ce qui est effectué par [CWinApp :: OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Pendant que l’application gère ON_COMMANDUPDATEUI notifications, les appels entrants sont gérés ultérieurement, une fois le traitement inactif terminé.

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a> COleMessageFilter::COleMessageFilter

Crée un objet `COleMessageFilter`.

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a> COleMessageFilter::EnableBusyDialog

Active et désactive la boîte de dialogue occupé, qui s’affiche lorsque le délai d’attente du message est dépassé (voir [SetRetryReply](#setretryreply)) pendant un appel OLE.

```cpp
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnableBusy*<br/>
Spécifie si la boîte de dialogue « occupé » est activée ou désactivée.

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a> COleMessageFilter::EnableNotRespondingDialog

Active et désactive la boîte de dialogue « pas de réponse », qui s’affiche si un message de clavier ou de souris est en attente pendant un appel OLE et que l’appel a expiré.

```cpp
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnableNotResponding*<br/>
Spécifie si la boîte de dialogue « pas de réponse » est activée ou désactivée.

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a> COleMessageFilter::EndBusyState

Appelez cette fonction pour terminer un état occupé.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Notes

Il fonctionne conjointement avec [BeginBusyState](#beginbusystate) pour contrôler l’état de disponibilité de l’application. La fonction [SetBusyReply](#setbusyreply) détermine la réponse de l’application à l’appel d’applications lorsqu’elle est occupée.

`BeginBusyState`Et `EndBusyState` appelle l’incrémentation et la décrémentation, respectivement, un compteur qui détermine si l’application est occupée. Par exemple, deux appels à `BeginBusyState` et un appel à ont `EndBusyState` toujours pour résultat un état occupé. Pour annuler un état occupé, il est nécessaire d’appeler `EndBusyState` le même nombre de fois que l’appel de la méthode `BeginBusyState` .

Par défaut, le Framework passe à l’état occupé pendant le traitement de l’inactivité, ce qui est effectué par [CWinApp :: OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Pendant que l’application gère ON_UPDATE_COMMAND_UI notifications, les appels entrants sont gérés à la fin du traitement inactif.

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a> COleMessageFilter::OnMessagePending

Appelé par l’infrastructure pour traiter des messages pendant qu’un appel OLE est en cours.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Pointeur vers le message en attente.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Lorsqu’une application appelante attend la fin d’un appel, le Framework appelle `OnMessagePending` avec un pointeur vers le message en attente. Par défaut, l’infrastructure distribue WM_PAINT messages, de sorte que les mises à jour de fenêtres peuvent se produire pendant un appel qui prend beaucoup de temps.

Vous devez inscrire votre filtre de messages au moyen d’un appel à [Register](#register) pour qu’il puisse devenir actif.

## <a name="colemessagefilterregister"></a><a name="register"></a> COleMessageFilter :: Register

Inscrit le filtre de messages avec les DLL système OLE.

```
BOOL Register();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un filtre de messages n’a aucun effet, sauf s’il est inscrit auprès des DLL système. En général, le code d’initialisation de votre application enregistre le filtre de messages de l’application. Tout autre filtre de messages inscrit par votre application doit être révoqué avant que le programme se termine par un appel à [Revoke](#revoke).

Le filtre de messages par défaut de l’infrastructure est automatiquement inscrit pendant l’initialisation et révoqué à l’arrêt.

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a> COleMessageFilter :: Revoke

Révoque une inscription précédente effectuée par un appel à [Register](#register).

```cpp
void Revoke();
```

### <a name="remarks"></a>Notes

Un filtre de messages doit être révoqué avant que le programme ne se termine.

Le filtre de messages par défaut, qui est créé et inscrit automatiquement par le Framework, est également révoqué automatiquement.

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a> COleMessageFilter::SetBusyReply

Cette fonction définit la « réponse occupée » de l’application.

```cpp
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>Paramètres

*nBusyReply*<br/>
Valeur de l' `SERVERCALL` énumération, qui est définie dans COMPOBJ. H. Il peut avoir l’une des valeurs suivantes :

- SERVERCALL_ISHANDLED l’application peut accepter des appels mais peut échouer lors du traitement d’un appel particulier.

- SERVERCALL_REJECTED l’application ne sera probablement jamais en mesure de traiter un appel.

- SERVERCALL_RETRYLATER l’application est temporairement dans un État dans lequel elle ne peut pas traiter un appel.

### <a name="remarks"></a>Notes

Les fonctions [BeginBusyState](#beginbusystate) et [EndBusyState](#endbusystate) contrôlent l’état occupé de l’application.

Quand une application est devenue occupée avec un appel à `BeginBusyState` , elle répond aux appels des DLL système OLE avec une valeur déterminée par le dernier paramètre de `SetBusyReply` . L’application appelante utilise cette réponse occupée pour déterminer l’action à entreprendre.

Par défaut, la réponse occupée est SERVERCALL_RETRYLATER. Cette réponse oblige l’application appelante à réessayer l’appel dès que possible.

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a> COleMessageFilter::SetMessagePendingDelay

Détermine la durée pendant laquelle l’application appelante attend une réponse de l’application appelée avant d’entreprendre une action supplémentaire.

```cpp
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>Paramètres

*nTimeout*<br/>
Nombre de millisecondes pour le délai d’attente du message.

### <a name="remarks"></a>Notes

Cette fonction fonctionne de concert avec [SetRetryReply](#setretryreply).

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a> COleMessageFilter::SetRetryReply

Détermine l’action de l’application appelante lorsqu’elle reçoit une réponse occupée d’une application appelée.

```cpp
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>Paramètres

*nRetryReply*<br/>
Nombre de millisecondes entre chaque tentative.

### <a name="remarks"></a>Notes

Lorsqu’une application appelée indique qu’elle est occupée, l’application appelante peut décider d’attendre que le serveur ne soit plus occupé, de réessayer immédiatement ou de réessayer après un intervalle spécifié. Il peut également décider d’annuler l’appel.

La réponse de l’appelant est contrôlée par les fonctions `SetRetryReply` et les [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply` détermine la durée pendant laquelle l’application appelante doit attendre entre les nouvelles tentatives pour un appel donné. `SetMessagePendingDelay` détermine la durée pendant laquelle l’application appelante attend une réponse du serveur avant d’entreprendre une action supplémentaire.

En règle générale, les valeurs par défaut sont acceptables et n’ont pas besoin d’être modifiées. Le Framework réessaie l’appel toutes les *nRetryReply* millisecondes jusqu’à ce que l’appel passe ou que le délai d’attente du message ait expiré. La valeur 0 pour *nRetryReply* spécifie une nouvelle tentative immédiate, et-1 spécifie l’annulation de l’appel.

Lorsque le délai d’attente du message est arrivé à expiration, la boîte de dialogue OLE « occupé » (voir [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) s’affiche afin que l’utilisateur puisse choisir d’annuler ou de réessayer l’appel. Appelez [EnableBusyDialog](#enablebusydialog) pour activer ou désactiver cette boîte de dialogue.

Lorsqu’un message de clavier ou de souris est en attente pendant un appel et que l’appel a expiré (a dépassé le délai d’attente du message), la boîte de dialogue « pas de réponse » s’affiche. Appelez [EnableNotRespondingDialog](#enablenotrespondingdialog) pour activer ou désactiver cette boîte de dialogue. Habituellement, cet État indique qu’une erreur s’est produite et que l’utilisateur est impatient.

Quand les boîtes de dialogue sont désactivées, la « nouvelle tentative de réponse » actuelle est toujours utilisée pour les appels aux applications occupées.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
