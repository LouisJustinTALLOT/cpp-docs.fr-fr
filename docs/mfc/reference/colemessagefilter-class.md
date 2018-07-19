---
title: COleMessageFilter, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a35f73405340b1ad66b004efcab49ac4c569c560
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852131"
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
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Active et désactive la boîte de dialogue qui s’affiche quand une application appelée ne répond pas.|  
|[COleMessageFilter::EndBusyState](#endbusystate)|Termine un état occupé de l’application.|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Appelé par l’infrastructure pour traiter les messages pendant un appel OLE est en cours.|  
|[COleMessageFilter::Register](#register)|Enregistre le filtre de messages avec les DLL système OLE.|  
|[COleMessageFilter::Revoke](#revoke)|Révoque l’inscription du filtre de message avec les DLL système OLE.|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Détermine la réponse de l’application occupé à un appel OLE.|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Détermine la durée pendant laquelle l’application attend une réponse à un appel OLE.|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|Détermine la réponse de l’application appelante pour une application occupée.|  
  
## <a name="remarks"></a>Notes  
 Le `COleMessageFilter` classe est utile dans les applications serveur et un conteneur visual éditions, ainsi que les applications OLE automation. Pour les applications serveur qui sont appelées, cette classe peut être utilisée pour rendre l’application « occupé » afin que les appels entrants à partir d’autres applications de conteneur sont soit annulées ou renouvelées plus tard. Cette classe peut également être utilisée pour déterminer l’action à prendre lorsque l’application appelante est occupée par une application appelante.  
  
 Utilisation courante est pour une application serveur pour appeler [BeginBusyState](#beginbusystate) et [EndBusyState](#endbusystate) quand il serait dangereux pour un document ou un autre objet accessible OLE à détruire. Ces appels sont effectués dans [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) pendant les mises à jour de l’interface utilisateur.  
  
 Par défaut, un `COleMessageFilter` objet est alloué lors de l’application est initialisée. Il peut être récupéré avec [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).  
  
 Il s’agit d’une classe avancée ; Vous devez rarement travailler directement dessus.  
  
 Pour plus d’informations, consultez l’article [serveurs : implémentation d’un serveur](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="beginbusystate"></a>  COleMessageFilter::BeginBusyState  
 Appelez cette fonction pour commencer un état occupé.  
  
```  
virtual void BeginBusyState();
```  
  
### <a name="remarks"></a>Notes  
 Il fonctionne conjointement avec [EndBusyState](#endbusystate) pour contrôler l’état occupé de l’application. La fonction [SetBusyReply](#setbusyreply) détermine la réponse de l’application aux applications appelantes lorsqu’il est occupé.  
  
 Le `BeginBusyState` et `EndBusyState` appels incrémenter et décrémenter, respectivement, un compteur qui détermine si l’application est occupée. Par exemple, deux appels à `BeginBusyState` et un seul appel à `EndBusyState` toujours le résultat dans un état occupé. Pour annuler un état occupé, il est nécessaire d’appeler `EndBusyState` le même nombre de fois `BeginBusyState` a été appelée.  
  
 Par défaut, l’infrastructure passe à l’état occupé pendant le traitement inactif, ce qui est effectué par [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Tandis que l’application gère les notifications ON_COMMANDUPDATEUI, les appels entrants sont gérées plus tard, après que traitement inactif est terminé.  
  
##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter  
 Crée un objet `COleMessageFilter`.  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog  
 Active et désactive la boîte de dialogue occupé, qui s’affiche lorsque le délai d’attente de message arrive à expiration (consultez [SetRetryReply](#setretryreply)) lors d’un appel OLE.  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bEnableBusy*  
 Spécifie si la boîte de dialogue « occupé » est activée ou désactivée.  
  
##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog  
 Active et désactive la boîte de dialogue « ne répond pas », qui s’affiche si un message de clavier ou la souris est en attente pendant OLE appel et l’appel a expiré.  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bEnableNotResponding*  
 Spécifie si la boîte de dialogue « ne répond pas » est activée ou désactivée.  
  
##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState  
 Appelez cette fonction pour mettre fin à un état occupé.  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>Notes  
 Il fonctionne conjointement avec [BeginBusyState](#beginbusystate) pour contrôler l’état occupé de l’application. La fonction [SetBusyReply](#setbusyreply) détermine la réponse de l’application aux applications appelantes lorsqu’il est occupé.  
  
 Le `BeginBusyState` et `EndBusyState` appels incrémenter et décrémenter, respectivement, un compteur qui détermine si l’application est occupée. Par exemple, deux appels à `BeginBusyState` et un seul appel à `EndBusyState` toujours le résultat dans un état occupé. Pour annuler un état occupé, il est nécessaire d’appeler `EndBusyState` le même nombre de fois `BeginBusyState` a été appelée.  
  
 Par défaut, l’infrastructure passe à l’état occupé pendant le traitement inactif, ce qui est effectué par [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Bien que l’application gère les notifications ON_UPDATE_COMMAND_UI, les appels entrants sont gérées issue du traitement inactif.  
  
##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending  
 Appelé par l’infrastructure pour traiter les messages pendant un appel OLE est en cours.  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 *pMsg*  
 Pointeur vers le message en attente.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’une application appelante est en attente pour un appel à être terminée, l’infrastructure appelle `OnMessagePending` avec un pointeur vers le message en attente. Par défaut, le framework distribue les messages WM_PAINT, afin que les mises à jour de la fenêtre peuvent se produire lors d’un appel qui prend un certain temps.  
  
 Vous devez enregistrer votre filtre de messages au moyen d’un appel à [inscrire](#register) avant qu’il peut devenir active.  
  
##  <a name="register"></a>  COleMessageFilter::Register  
 Enregistre le filtre de messages avec les DLL système OLE.  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un filtre de messages n’a aucun effet, sauf si elle est inscrite avec les DLL système. Code d’initialisation de votre application enregistre généralement un filtre de messages de l’application. Tout autre filtre de message enregistré par votre application doit être révoqué avant le programme se termine par un appel à [révoquer](#revoke).  
  
 Filtre de message par défaut de l’infrastructure est automatiquement enregistré lors de l’initialisation et révoqué à la fin.  
  
##  <a name="revoke"></a>  COleMessageFilter::Revoke  
 Révoque une inscription précédente effectuée par un appel à [inscrire](#register).  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Notes  
 Un filtre de messages doit être révoqué avant le programme se termine.  
  
 Le filtre de message par défaut, qui est créé et inscrit automatiquement par l’infrastructure, est automatiquement révoqué.  
  
##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply  
 Cette fonction affecte « occupé reply. » l’application  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>Paramètres  
 *nBusyReply*  
 Une valeur comprise entre le `SERVERCALL` énumération, qui est définie dans COMPOBJ. H. Il peut avoir l’une des valeurs suivantes :  
  
- SERVERCALL_ISHANDLED l’application peut accepter des appels, mais peut échouer lors du traitement d’un appel particulier.  
  
- L’application de SERVERCALL_REJECTED probablement jamais sera en mesure de traiter un appel.  
  
- SERVERCALL_RETRYLATER l’application est temporairement dans un état dans lequel il ne peut pas traiter un appel.  
  
### <a name="remarks"></a>Notes  
 Le [BeginBusyState](#beginbusystate) et [EndBusyState](#endbusystate) fonctions contrôlent l’état occupé de l’application.  
  
 Quand une application a été effectuée occupée par un appel à `BeginBusyState`, il répond aux appels à partir de la DLL du système OLE avec une valeur déterminée par le dernier paramètre de `SetBusyReply`. L’application appelante utilise cette réponse occupée pour déterminer l’action à entreprendre.  
  
 Par défaut, la réponse occupée est SERVERCALL_RETRYLATER. Cette réponse, l’application appelante renouveler l’appel dès que possible.  
  
##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay  
 Détermine la durée pendant laquelle l’application appelante attend une réponse de l’application appelée avant d’entreprendre une action supplémentaire.  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>Paramètres  
 *%ndélai*  
 Nombre de millisecondes que le délai d’attente de message.  
  
### <a name="remarks"></a>Notes  
 Cette fonction fonctionne conjointement avec [SetRetryReply](#setretryreply).  
  
##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply  
 Détermine l’action de l’application appelante lorsqu’il reçoit une réponse occupé à partir d’une application appelée.  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *nRetryReply*  
 Nombre de millisecondes entre chaque tentative.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’une application appelée indique qu’il est occupé, l’application appelante peut décider d’attendre que le serveur n’est plus occupé, nouvelle tentative immédiatement ou après un intervalle spécifié. Il peut également décider d’annuler l’appel complètement.  
  
 Réponse de l’appelant est contrôlé par les fonctions `SetRetryReply` et [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply` Détermine la durée pendant laquelle l’application appelante doit attendre entre les nouvelles tentatives pour un appel donné. `SetMessagePendingDelay` Détermine la durée pendant laquelle l’application appelante attend une réponse à partir du serveur avant d’entreprendre une autre action.  
  
 Généralement, les valeurs par défaut sont acceptables et n’avez pas besoin d’être modifié. Le framework retente l’appel chaque *nRetryReply* millisecondes jusqu'à ce que l’appel passe par ou le délai d’attente de message a expiré. La valeur 0 pour *nRetryReply* spécifie une nouvelle tentative immédiate et - 1 indique l’annulation de l’appel.  
  
 Lorsque le délai d’attente de message a expiré, OLE « occupé la boîte de dialogue » (voir [classe COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) s’affiche afin que l’utilisateur peut choisir d’annuler ou de renouveler l’appel. Appelez [EnableBusyDialog](#enablebusydialog) pour activer ou désactiver cette boîte de dialogue.  
  
 Quand un message de clavier ou la souris est en attente pendant un appel et l’appel a expiré (a dépassé le délai d’attente de message), la boîte de dialogue « ne répond pas » s’affiche. Appelez [EnableNotRespondingDialog](#enablenotrespondingdialog) pour activer ou désactiver cette boîte de dialogue. Cette situation justifie indique généralement qu’une erreur s’est produite et que l’utilisateur est bien impatiente.  
  
 Lorsque les boîtes de dialogue sont désactivés, le cours « réessayer réponse » est toujours utilisé pour les appels aux applications occupées.  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
