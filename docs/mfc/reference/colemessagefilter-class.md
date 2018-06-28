---
title: Classe de l’intermédiaire de COleMessageFilter | Documents Microsoft
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
ms.openlocfilehash: f758a3cc82d4f6cfcc28f89ae206a82b899c0042
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037609"
---
# <a name="colemessagefilter-class"></a>Classe de l’intermédiaire de COleMessageFilter
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
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Met l’application dans l’état de disponibilité.|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Active ou désactive la boîte de dialogue qui s’affiche quand une application appelée est occupée.|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Active ou désactive la boîte de dialogue qui s’affiche lorsqu’une application appelée ne répond pas.|  
|[COleMessageFilter::EndBusyState](#endbusystate)|Arrête l’état de disponibilité de l’application.|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Appelé par l’infrastructure pour traiter les messages pendant un appel OLE est en cours d’exécution.|  
|[COleMessageFilter::Register](#register)|Enregistre le filtre de messages avec les DLL système OLE.|  
|[COleMessageFilter::Revoke](#revoke)|Révoque l’inscription du filtre de message avec les DLL système OLE.|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Détermine la réponse de l’application occupé à un appel OLE.|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Détermine la durée pendant laquelle l’application attend une réponse à un appel OLE.|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|Détermine la réponse de l’application appelante à une application occupée.|  
  
## <a name="remarks"></a>Notes  
 La `COleMessageFilter` classe est utile dans les applications serveur et un conteneur éditions visuelle, ainsi que les applications OLE automation. Pour les applications serveur qui sont appelées, cette classe peut être utilisée pour rendre l’application « occupé » afin que les appels entrants à partir d’autres applications de conteneur sont soit annulées ou renouvelées plus tard. Cette classe peut également être utilisée pour déterminer l’action à prendre lorsque l’application appelée est occupée par une application appelante.  
  
 Utilisation commune consiste pour une application serveur à appeler [BeginBusyState](#beginbusystate) et [EndBusyState](#endbusystate) quand il serait dangereux pour un document ou un autre objet accessible OLE d’être détruites. Ces appels sont effectués dans [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) pendant les mises à jour de l’interface utilisateur.  
  
 Par défaut, un `COleMessageFilter` objet est alloué lors de l’initialisation de l’application. Il peut être récupéré avec [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).  
  
 Il s’agit d’une classe avancée ; Vous devez rarement travailler directement avec lui.  
  
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
 Il fonctionne conjointement avec [EndBusyState](#endbusystate) pour contrôler l’état de disponibilité de l’application. La fonction [SetBusyReply](#setbusyreply) détermine la réponse de l’application aux applications appelantes lorsqu’il est occupé.  
  
 Le `BeginBusyState` et `EndBusyState` appels incrémenter et décrémenter, respectivement, un compteur qui détermine si l’application est occupée. Par exemple, deux appels à `BeginBusyState` et un appel à `EndBusyState` toujours le résultat dans un état de disponibilité. Pour annuler un état occupé, il est nécessaire d’appeler `EndBusyState` le même nombre de fois `BeginBusyState` a été appelée.  
  
 Par défaut, l’infrastructure passe à l’état occupé pendant le traitement inactif, ce qui est effectué par [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Pendant que l’application gère les notifications ON_COMMANDUPDATEUI, les appels entrants sont gérés plus tard, après que le traitement inactif est terminé.  
  
##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter  
 Crée un objet `COleMessageFilter`.  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog  
 Active ou désactive la boîte de dialogue occupé, ce qui s’affiche lorsque le délai d’attente de message expire (consultez [SetRetryReply](#setretryreply)) lors d’un appel OLE.  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bEnableBusy*  
 Spécifie si la boîte de dialogue « occupé » est activée ou désactivée.  
  
##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog  
 Active ou désactive la boîte de dialogue « ne répond pas », qui s’affiche si un message du clavier ou de la souris est en attente pendant une OLE appel et l’appel a expiré.  
  
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
 Il fonctionne conjointement avec [BeginBusyState](#beginbusystate) pour contrôler l’état de disponibilité de l’application. La fonction [SetBusyReply](#setbusyreply) détermine la réponse de l’application aux applications appelantes lorsqu’il est occupé.  
  
 Le `BeginBusyState` et `EndBusyState` appels incrémenter et décrémenter, respectivement, un compteur qui détermine si l’application est occupée. Par exemple, deux appels à `BeginBusyState` et un appel à `EndBusyState` toujours le résultat dans un état de disponibilité. Pour annuler un état occupé, il est nécessaire d’appeler `EndBusyState` le même nombre de fois `BeginBusyState` a été appelée.  
  
 Par défaut, l’infrastructure passe à l’état occupé pendant le traitement inactif, ce qui est effectué par [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Pendant que l’application gère les notifications ON_UPDATE_COMMAND_UI, les appels entrants sont gérées à l’issue du traitement inactif.  
  
##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending  
 Appelé par l’infrastructure pour traiter les messages pendant un appel OLE est en cours d’exécution.  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 *pMsg*  
 Pointeur vers le message en attente.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’une application appelante est en attente pour un appel doit être terminé, le framework appelle `OnMessagePending` avec un pointeur vers le message en attente. Par défaut, le framework distribue des messages WM_PAINT, afin que les mises à jour de la fenêtre peuvent se produire lors d’un appel qui prend beaucoup de temps.  
  
 Vous devez enregistrer votre filtre de messages au moyen d’un appel à [inscrire](#register) avant qu’il peut devenir actif.  
  
##  <a name="register"></a>  COleMessageFilter::Register  
 Enregistre le filtre de messages avec les DLL système OLE.  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un filtre de messages n’a aucun effet, sauf si elle est inscrite avec les DLL système. Code d’initialisation de votre application enregistre généralement le filtre de messages de l’application. Tout autre filtre de message enregistré par votre application doit être révoqué avant le programme se termine par un appel à [révoquer](#revoke).  
  
 Filtre de message par défaut de l’infrastructure est automatiquement enregistré lors de l’initialisation et révoqué à la fin.  
  
##  <a name="revoke"></a>  COleMessageFilter::Revoke  
 Révoque une inscription précédente effectuée par un appel à [inscrire](#register).  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Notes  
 Un filtre de messages doit être révoqué avant la fin du programme.  
  
 Le filtre de message par défaut, qui est créé et inscrit automatiquement par l’infrastructure, est automatiquement révoqué.  
  
##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply  
 Cette fonction affecte à « occupé reply. » l’application  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>Paramètres  
 *nBusyReply*  
 Une valeur à partir de la `SERVERCALL` énumération, qui est définie dans COMPOBJ. H. Il peut avoir l’une des valeurs suivantes :  
  
- **SERVERCALL_ISHANDLED** l’application peut accepter des appels mais risque d’échouer lors du traitement d’un appel particulier.  
  
- **SERVERCALL_REJECTED** l’application probablement jamais sera en mesure de traiter un appel.  
  
- **SERVERCALL_RETRYLATER** l’application est temporairement dans un état dans lequel elle ne peut pas traiter un appel.  
  
### <a name="remarks"></a>Notes  
 Le [BeginBusyState](#beginbusystate) et [EndBusyState](#endbusystate) fonctions contrôlent l’état de disponibilité de l’application.  
  
 Lorsqu’une application a été effectuée occupée par un appel à `BeginBusyState`, il répond aux appels à partir de la DLL du système OLE avec une valeur déterminée par le dernier paramètre de `SetBusyReply`. L’application appelante utilise cette réponse occupée pour déterminer l’action à entreprendre.  
  
 Par défaut, la réponse occupée est **SERVERCALL_RETRYLATER**. Cette réponse provoque l’application appelante renouveler l’appel dès que possible.  
  
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
 Détermine l’action de l’application appelante lorsqu’il reçoit une réponse occupée à partir d’une application appelée.  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *nRetryReply*  
 Nombre de millisecondes entre les tentatives.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’une application appelée indique qu’il est occupé, l’application appelante peut décider d’attendre que le serveur n’est plus occupé, nouvelle tentative immédiatement ou après un intervalle spécifié. Il peut également décider d’annuler l’appel complètement.  
  
 Réponse de l’appelant est contrôlé par les fonctions `SetRetryReply` et [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply` Détermine la durée pendant laquelle l’application appelante doit attendre entre les nouvelles tentatives pour un appel donné. `SetMessagePendingDelay` Détermine la durée pendant laquelle l’application appelante attend une réponse du serveur avant d’entreprendre d’action supplémentaire.  
  
 Généralement, les valeurs par défaut sont acceptables et n’avez pas besoin d’être modifié. Le framework retente l’appel de chaque *nRetryReply* millisecondes jusqu'à ce que l’appel ou le délai d’attente de messages a expiré. La valeur 0 pour *nRetryReply* spécifie une nouvelle tentative immédiate et - 1 indique l’annulation de l’appel.  
  
 Lorsque le délai d’attente de message a expiré, OLE « occupé la boîte de dialogue » (voir [classe COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) s’affiche afin que l’utilisateur peut choisir d’annuler ou de renouveler l’appel. Appelez [EnableBusyDialog](#enablebusydialog) pour activer ou désactiver cette boîte de dialogue.  
  
 Lorsqu’un message de clavier ou de la souris est en attente pendant un appel et l’appel a expiré (a dépassé le délai d’attente de message), la boîte de dialogue « ne répond pas » s’affiche. Appelez [EnableNotRespondingDialog](#enablenotrespondingdialog) pour activer ou désactiver cette boîte de dialogue. Cet état indique généralement qu’un problème et que l’utilisateur est mise en route impatient.  
  
 Lorsque les boîtes de dialogue sont désactivées, l’actuel « réessayer la réponse » est toujours utilisé pour les appels à des applications occupées.  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
