---
title: CWinThread (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
dev_langs:
- C++
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7cbdcc1c5534d8dd9ba5d4f895af70a8ec16ac5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376964"
---
# <a name="cwinthread-class"></a>CWinThread (classe)
Représente un thread d'exécution dans une application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWinThread : public CCmdTarget  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinThread::CWinThread](#cwinthread)|Construit un objet `CWinThread`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinThread::CreateThread](#createthread)|Démarre l’exécution d’un `CWinThread` objet.|  
|[CWinThread::ExitInstance](#exitinstance)|Substituez pour nettoyer votre thread se termine.|  
|[CWinThread::GetMainWnd](#getmainwnd)|Récupère un pointeur vers la fenêtre principale pour le thread.|  
|[CWinThread::GetThreadPriority](#getthreadpriority)|Obtient la priorité du thread actuel.|  
|[CWinThread::InitInstance](#initinstance)|Remplacement pour effectuer une initialisation instance thread.|  
|[CWinThread::IsIdleMessage](#isidlemessage)|Recherche les messages spéciaux.|  
|[CWinThread::OnIdle](#onidle)|Substituez pour effectuer le traitement des temps d’inactivité spécifique au thread.|  
|[CWinThread::PostThreadMessage](#postthreadmessage)|Publie un message à un autre `CWinThread` objet.|  
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtre les messages avant qu’ils sont distribués aux fonctions Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Intercepte certains messages avant qu’ils atteignent l’application.|  
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Intercepte toutes les exceptions non gérées levées par les messages du thread et les gestionnaires de commandes.|  
|[CWinThread::PumpMessage](#pumpmessage)|Contient la boucle de messages du thread.|  
|[CWinThread::ResumeThread](#resumethread)|Décrémente un du thread compteur de suspension.|  
|[CWinThread::Run](#run)|Fonction de contrôle pour les threads avec une pompe de messages. Substituez pour personnaliser la boucle de messages par défaut.|  
|[CWinThread::SetThreadPriority](#setthreadpriority)|Définit la priorité du thread actuel.|  
|[CWinThread::SuspendThread](#suspendthread)|Incrémente un du thread compteur de suspension.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinThread::operator descripteur](#operator_handle)|Récupère le handle de la `CWinThread` objet.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Spécifie s’il faut détruire l’objet à l’arrêt du thread.|  
|[CWinThread::m_hThread](#m_hthread)|Handle vers le thread actuel.|  
|[CWinThread::m_nThreadID](#m_nthreadid)|ID du thread actuel.|  
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Pointeur vers la fenêtre principale de l’application conteneur lorsqu’un serveur OLE est actif en place.|  
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Contient un pointeur vers la fenêtre principale de l’application.|  
  
## <a name="remarks"></a>Notes  
 Le thread principal de l’exécution est généralement fourni par un objet dérivé `CWinApp`; `CWinApp` est dérivée de `CWinThread`. Supplémentaires `CWinThread` objets autorisant plusieurs threads dans une application donnée.  
  
 Il existe deux types généraux de threads qui `CWinThread` prend en charge : threads de travail et les threads d’interface utilisateur. Threads de travail ne possède aucun pompe de messages : par exemple, un thread qui effectue des calculs d’arrière-plan dans une application de la feuille de calcul. Threads d’interface utilisateur ont une pompe de messages et traitent les messages reçus à partir du système. [CWinApp](../../mfc/reference/cwinapp-class.md) et classes dérivées sont des exemples de threads d’interface utilisateur. Autres threads d’interface utilisateur peuvent également être dérivés directement `CWinThread`.  
  
 Objets de la classe `CWinThread` généralement existent pour la durée du thread. Si vous souhaitez modifier ce comportement, affectez [m_bAutoDelete](#m_bautodelete) à **FALSE**.  
  
 La `CWinThread` classe est nécessaire pour rendre votre code et MFC complètement thread-safe. Données locales de thread utilisées par l’infrastructure pour mettre à jour les informations spécifiques au thread sont gérées par `CWinThread` objets. En raison de cette dépendance sur `CWinThread` pour gérer les données locales de thread, n’importe quel thread qui utilise MFC doit être créée par MFC. Par exemple, un thread créé par la fonction de l’exécution [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) ne peut pas utiliser les API de MFC.  
  
 Pour créer un thread, appelez [AfxBeginThread](application-information-and-management.md#afxbeginthread). Il existe deux formes, selon que vous souhaitez un thread de travail ou d’interface utilisateur. Si vous souhaitez un thread d’interface utilisateur, passez à `AfxBeginThread` un pointeur vers le `CRuntimeClass` de votre `CWinThread`-classe dérivée. Si vous souhaitez créer un thread de travail, passez à `AfxBeginThread` un pointeur vers la fonction de contrôle et le paramètre à la fonction de contrôle. Pour les threads de travail et les threads d’interface utilisateur, vous pouvez spécifier des paramètres facultatifs qui modifient la priorité, la taille de pile, indicateurs de création et les attributs de sécurité. `AfxBeginThread` Retourne un pointeur vers votre nouvelle `CWinThread` objet.  
  
 Au lieu d’appeler `AfxBeginThread`, vous pouvez construire un `CWinThread`-dérivée d’objet, puis appelez `CreateThread`. Cette méthode de construction en deux étapes est utile si vous souhaitez réutiliser le `CWinThread` objet entre la création successive et arrêts d’exécutions de thread.  
  
 Pour plus d’informations sur `CWinThread`, consultez les articles [Multithreading à l’aide de C++ et MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading : création de Threads d’Interface utilisateur](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading : création d’un travail Threads](../../parallel/multithreading-creating-worker-threads.md), et [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="createthread"></a>  CWinThread::CreateThread  
 Crée un thread s’exécute dans l’espace d’adressage du processus appelant.  
  
```  
BOOL CreateThread(
    DWORD dwCreateFlags = 0,  
    UINT nStackSize = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwCreateFlags`  
 Spécifie un indicateur supplémentaire qui contrôle la création du thread. Cet indicateur peut contenir une des deux valeurs :  
  
- **CREATE_SUSPENDED** démarrage du thread avec un compteur de suspension d’un. Utilisez **CREATE_SUSPENDED** si vous souhaitez initialiser les données de membre de la `CWinThread` de l’objet, tel que [m_bAutoDelete](#m_bautodelete) ou tous les membres de votre classe dérivée, avant que le thread commence à s’exécuter. Une fois que votre initialisation est terminée, utilisez le [CWinThread::ResumeThread](#resumethread) pour démarrer le thread en cours d’exécution. Le thread s’exécute pas jusqu'à ce que `CWinThread::ResumeThread` est appelée.  
  
- **0** démarrer le thread immédiatement après sa création.  
  
 `nStackSize`  
 Spécifie la taille en octets de la pile pour le nouveau thread. Si **0**, la taille de pile par défaut est la même taille que le thread du processus principal.  
  
 `lpSecurityAttrs`  
 Pointe vers un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) structure qui spécifie les attributs de sécurité pour le thread.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le thread est créé avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez `AfxBeginThread` pour créer un objet thread et exécutez-le en une seule étape. Utilisez `CreateThread` si vous souhaitez réutiliser l’objet thread entre successive création et l’arrêt d’exécutions de thread.  
  
##  <a name="cwinthread"></a>  CWinThread::CWinThread  
 Construit un objet `CWinThread`.  
  
```  
CWinThread();
```  
  
### <a name="remarks"></a>Notes  
 Pour commencer l’exécution du thread, appelez le [CreateThread](#createthread) fonction membre. Vous allez créer généralement des threads en appelant [AfxBeginThread](application-information-and-management.md#afxbeginthread), qui appelle ce constructeur et `CreateThread`.  
  
##  <a name="exitinstance"></a>  CWinThread::ExitInstance  
 Appelé par l’infrastructure à partir de rarement substituée [exécuter](#run) fonction membre pour quitter cette instance du thread, ou si un appel à [InitInstance](#initinstance) échoue.  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Code de sortie du thread ; 0 n’indique aucune erreur et les valeurs supérieures à 0 indiquent une erreur. Cette valeur peut être récupérée en appelant [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Notes  
 N’appelez pas cette fonction membre à partir de n’importe quel emplacement, mais dans le **exécuter** fonction membre. Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur.  
  
 L’implémentation par défaut de cette fonction supprime le `CWinThread` si l’objet [m_bAutoDelete](#m_bautodelete) est **TRUE**. Remplacez cette fonction si vous souhaitez effectuer un nettoyage supplémentaire quand votre thread se termine. Votre implémentation de `ExitInstance` doit appeler la version de la classe de base après l’exécution de votre code.  
  
##  <a name="getmainwnd"></a>  CWinThread::GetMainWnd  
 Si votre application est un serveur OLE, appelez cette fonction pour récupérer un pointeur vers la fenêtre principale active de l’application plutôt que directement référence à la `m_pMainWnd` membre de l’objet application.  
  
```  
virtual CWnd* GetMainWnd();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Cette fonction retourne un pointeur vers un des deux types de fenêtres. Si votre thread fait partie d’un serveur OLE et dispose d’un objet qui est actif sur place à l’intérieur d’un conteneur actif, cette fonction retourne le [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) membre de données de la `CWinThread` objet.  
  
 Si aucun objet qui est actif en place dans un conteneur ou de votre application n’est pas un serveur OLE, cette fonction retourne le [m_pMainWnd](#m_pmainwnd) membre de données de votre objet de thread.  
  
### <a name="remarks"></a>Notes  
 Pour les threads d’interface utilisateur, cela est équivalent à la référence directe à la `m_pActiveWnd` membre de votre objet application.  
  
 Si votre application n’est pas un serveur OLE, appel de cette fonction est équivalent à la référence directe à la `m_pMainWnd` membre de votre objet application.  
  
 Remplacez cette fonction pour modifier le comportement par défaut.  
  
##  <a name="getthreadpriority"></a>  CWinThread::GetThreadPriority  
 Obtient le niveau de priorité de thread en cours de ce thread.  
  
```  
int GetThreadPriority();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Niveau de la priorité de thread actuel dans sa classe de priorité. La valeur retournée sera une des valeurs suivantes, répertoriées à partir de la priorité la plus élevée à la plus faible :  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **NIVEAU DE PRIORITÉ**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Pour plus d’informations sur ces priorités, consultez [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) dans le Kit de développement logiciel Windows.  
  
##  <a name="initinstance"></a>  CWinThread::InitInstance  
 `InitInstance` doit être remplacée pour initialiser chaque nouvelle instance d’un thread d’interface utilisateur.  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’initialisation a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 En règle générale, vous substituez `InitInstance` pour effectuer des tâches qui doivent être effectuées lorsque vous créez un thread.  
  
 Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur. Effectuer l’initialisation de threads de travail dans la fonction de contrôle passée à [AfxBeginThread](application-information-and-management.md#afxbeginthread).  
  
##  <a name="isidlemessage"></a>  CWinThread::IsIdleMessage  
 Remplacez cette fonction pour conserver **OnIdle** d’être appelée après la génération des messages spécifiques.  
  
```  
virtual BOOL IsIdleMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 `pMsg`  
 Pointe vers le message actuel en cours de traitement.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si `OnIdle` doit être appelée après le traitement de message, sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut n’appelle pas **OnIdle** après les messages de la souris redondants et des messages générés en faisant clignoter signes.  
  
 Si une application a créé un minuteur court, **OnIdle** sera appelée fréquemment, à l’origine des problèmes de performances. Pour améliorer les performances d’une telle application, vous devez substituer `IsIdleMessage` dans l’application `CWinApp`-classe dont vous recherchez dérivée `WM_TIMER` messages comme suit :  
  
 [!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]  
  
 La gestion des `WM_TIMER` de cette façon améliore les performances des applications qui utilisent des minuteries courts.  
  
##  <a name="m_bautodelete"></a>  CWinThread::m_bAutoDelete  
 Spécifie si le `CWinThread` objet doit être supprimé automatiquement à l’arrêt du thread.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Notes  
 Le `m_bAutoDelete` membre de données est une variable publique de type **BOOL**.  
  
 La valeur de `m_bAutoDelete` n’affecte pas la façon dont le handle du thread sous-jacent est fermé. Le handle du thread est fermé toujours lorsque le `CWinThread` objet est détruit.  
  
##  <a name="m_hthread"></a>  CWinThread::m_hThread  
 Pointeur vers le thread associé à ce `CWinThread`.  
  
```  
HANDLE m_hThread;  
```  
  
### <a name="remarks"></a>Notes  
 Le `m_hThread` membre de données est une variable publique de type `HANDLE`. Il est valide uniquement si sous-jacent thread actuellement existe.  
  
##  <a name="m_nthreadid"></a>  CWinThread::m_nThreadID  
 ID du thread associé à ce `CWinThread`.  
  
```  
DWORD m_nThreadID;  
```  
  
### <a name="remarks"></a>Notes  
 Le **m_nThreadID** membre de données est une variable publique de type `DWORD`. Il est valide uniquement si sous-jacent thread actuellement existe.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [AfxGetThread](application-information-and-management.md#afxgetthread).  
  
##  <a name="m_pactivewnd"></a>  CWinThread::m_pActiveWnd  
 Utilisez ce membre de données pour stocker un pointeur vers l’objet de la fenêtre active de votre thread.  
  
```  
CWnd* m_pActiveWnd;  
```  
  
### <a name="remarks"></a>Notes  
 La bibliothèque Microsoft Foundation Class mettra fin automatiquement à votre thread lorsque la fenêtre référencée par `m_pActiveWnd` est fermé. Si ce thread est le thread principal d’une application, l’application sera également terminée. Si ce membre de données est **NULL**, la fenêtre active de l’application `CWinApp` objet est hérité. `m_pActiveWnd` est une variable publique de type **CWnd\***.  
  
 En général, vous définissez cette variable membre lorsque vous substituez `InitInstance`. Dans un thread de travail, la valeur de ce membre de données est héritée de son thread parent.  
  
##  <a name="m_pmainwnd"></a>  CWinThread::m_pMainWnd  
 Utilisez ce membre de données pour stocker un pointeur vers l’objet de fenêtre principale de votre thread.  
  
```  
CWnd* m_pMainWnd;  
```  
  
### <a name="remarks"></a>Notes  
 La bibliothèque Microsoft Foundation Class mettra fin automatiquement à votre thread lorsque la fenêtre référencée par `m_pMainWnd` est fermé. Si ce thread est le thread principal d’une application, l’application sera également terminée. Si ce membre de données est **NULL**, la fenêtre principale de l’application `CWinApp` objet permet de déterminer le moment terminer la thread. `m_pMainWnd` est une variable publique de type **CWnd\***.  
  
 En général, vous définissez cette variable membre lorsque vous substituez `InitInstance`. Dans un thread de travail, la valeur de ce membre de données est héritée de son thread parent.  
  
##  <a name="onidle"></a>  CWinThread::OnIdle  
 Remplacez cette fonction membre pour effectuer le traitement des temps d’inactivité.  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>Paramètres  
 `lCount`  
 Un compteur incrémenté à chaque `OnIdle` est appelée lorsque la file d’attente de messages du thread est vide. Ce nombre est réinitialisé à 0 à chaque fois qu’un nouveau message est traité. Vous pouvez utiliser la `lCount` paramètre pour déterminer la longueur relative de temps que le thread a été inactif sans traitement d’un message.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro pour recevoir plus le temps de traitement inactif ; 0 si vous n’y a plus de temps de traitement inactif est nécessaire.  
  
### <a name="remarks"></a>Notes  
 `OnIdle` est appelée dans la boucle de message par défaut lors de la file d’attente de messages du thread est vide. Utilisez votre remplacement pour appeler votre propre arrière-plan tâches du Gestionnaire des temps d’inactivité.  
  
 `OnIdle` Renvoie 0 pour indiquer qu’aucun temps de traitement inactif supplémentaire n’est nécessaire. Le `lCount` paramètre est incrémenté chaque fois que `OnIdle` est appelée lorsque la file d’attente est vide et est réinitialisé à 0, chaque fois qu’un nouveau message est traité. Vous pouvez appeler vos routines inactifs différents en fonction de ce nombre.  
  
 L’implémentation par défaut de cette fonction membre libère des objets temporaires et des bibliothèques de liens dynamiques inutilisé de la mémoire.  
  
 Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur.  
  
 Étant donné que l’application ne peut pas traiter les messages jusqu'à ce que `OnIdle` retourne, n’effectuez pas de tâches de longue durée dans cette fonction.  
  
##  <a name="operator_handle"></a>  CWinThread::operator descripteur  
 Récupère le handle de la `CWinThread` objet.  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, le handle de l’objet thread. dans le cas contraire, **NULL**.  
  
### <a name="remarks"></a>Notes  
 Utilisez la poignée pour appeler directement des API Windows.  
  
##  <a name="postthreadmessage"></a>  CWinThread::PostThreadMessage  
 Appelé pour valider un message défini par l’utilisateur à un autre `CWinThread` objet.  
  
```  
BOOL PostThreadMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Paramètres  
 `message`  
 ID du message défini par l’utilisateur.  
  
 `wParam`  
 Premier paramètre de message.  
  
 `lParam`  
 Deuxième paramètre de message.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le message publié est mappé au Gestionnaire de messages approprié par la macro de mappage de message `ON_THREAD_MESSAGE`.  
  
> [!NOTE]
>  Lors de l’appel Windows [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946) fonction d’une application MFC, le message MFC gestionnaires ne sont pas appelés. Pour plus d’informations, consultez l’article de la Base de connaissances, « PRB : MFC Message Gestionnaire pas appelée avec PostThreadMessage() » (Q142415).  
  
##  <a name="pretranslatemessage"></a>  CWinThread::PreTranslateMessage  
 Remplacez cette fonction pour filtrer les messages de fenêtre avant d’être distribués aux fonctions Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 `pMsg`  
 Pointe vers un [MSG, structure](../../mfc/reference/msg-structure1.md) contenant le message à traiter.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le message a été entièrement traité dans `PreTranslateMessage` et ne doit pas être traitée ultérieurement. Zéro si le message doit être traité de façon normale.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur.  
  
##  <a name="processmessagefilter"></a>  CWinThread::ProcessMessageFilter  
 La fonction de raccordement de l’infrastructure appelle cette fonction membre pour filtrer et répondre à certains messages Windows.  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 `code`  
 Spécifie un code de raccordement. Cette fonction membre utilise le code pour déterminer comment traiter `lpMsg.`  
  
 `lpMsg`  
 Un pointeur vers un Windows [MSG, structure](../../mfc/reference/msg-structure1.md).  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le message est traité ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Une fonction de raccordement traite les événements avant leur envoi à un message normal de l’application de traitement.  
  
 Si vous remplacez cette fonctionnalité avancée, veillez à appeler la version classe de base pour mettre à jour de l’infrastructure de raccordement de traitement.  
  
##  <a name="processwndprocexception"></a>  CWinThread::ProcessWndProcException  
 L’infrastructure appelle cette fonction membre chaque fois que le gestionnaire n’intercepte pas d’une exception levée dans les messages de votre thread ou les gestionnaires de commandes.  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 *e*  
 Pointe vers une exception non gérée.  
  
 `pMsg`  
 Pointe vers un [MSG, structure](../../mfc/reference/msg-structure1.md) contenant des informations sur le message windows qui a provoqué l’infrastructure pour lever une exception.  
  
### <a name="return-value"></a>Valeur de retour  
 -1 si une `WM_CREATE` exception est générée ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 N’appelez pas cette fonction membre directement.  
  
 L’implémentation par défaut de cette fonction membre gère uniquement les exceptions générées à partir des messages suivants :  
  
|Commande|Action|  
|-------------|------------|  
|`WM_CREATE`|En cas d’échec.|  
|`WM_PAINT`|Valider la fenêtre affectée, empêchant ainsi un autre `WM_PAINT` message d’être générée.|  
  
 Remplacez cette fonction membre pour fournir la gestion globale de vos exceptions. Appelez la fonctionnalité de base uniquement si vous souhaitez afficher le comportement par défaut.  
  
 Cette fonction membre est utilisée uniquement dans les threads qui ont une pompe de messages.  
  
##  <a name="pumpmessage"></a>  CWinThread::PumpMessage  
 Contient la boucle de messages du thread.  
  
```  
virtual BOOL PumpMessage();
```  
  
### <a name="remarks"></a>Notes  
 `PumpMessage` Contient la boucle de messages du thread. **PumpMessage ne** est appelée par `CWinThread` pour pomper les messages du thread. Vous pouvez appeler `PumpMessage` directement pour forcer les messages à traiter, ou vous pouvez remplacer `PumpMessage` pour modifier son comportement par défaut.  
  
 Appel de `PumpMessage` directement et est recommandé de remplacer son comportement par défaut pour les utilisateurs expérimentés uniquement.  
  
##  <a name="resumethread"></a>  CWinThread::ResumeThread  
 Appelé pour reprendre l’exécution d’un thread qui a été suspendue par la [SuspendThread](#suspendthread) fonction membre ou un thread créé avec la **CREATE_SUSPENDED** indicateur.  
  
```  
DWORD ResumeThread();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le thread du précédent suspendre le nombre de cas de réussite ; `0xFFFFFFFF` dans le cas contraire. Si la valeur de retour est zéro, le thread actuel n’a pas suspendu. Si la valeur de retour est un, le thread a été suspendu, mais il est maintenant de redémarrer. Toute valeur de retour supérieure à 1 signifie le thread reste suspendue.  
  
### <a name="remarks"></a>Notes  
 Le compteur de suspension du thread actuel est réduit d’une unité. Si le compteur de suspension est réduit à zéro, le thread reprend l’exécution ; dans le cas contraire, le thread reste suspendu.  
  
##  <a name="run"></a>  CWinThread::Run  
 Fournit une boucle de message par défaut pour les threads d’interface utilisateur.  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `int` valeur retournée par le thread. Cette valeur peut être récupérée en appelant [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Notes  
 **Exécutez** acquiert et distribue des messages Windows jusqu'à ce que l’application reçoit un [WM_QUIT](http://msdn.microsoft.com/library/windows/desktop/ms632641) message. Si la file d’attente de messages du thread ne contient actuellement aucun message, **exécuter** appelle `OnIdle` pour effectuer le traitement des temps d’inactivité. Les messages entrants atteindre le [PreTranslateMessage](#pretranslatemessage) fonction membre pour un traitement spécial, puis à la fonction [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) pour la traduction de clavier standard. Enfin, le [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows est appelée.  
  
 **Exécutez** est rarement substituée, mais vous pouvez remplacer cette méthode pour implémenter un comportement spécial.  
  
 Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur.  
  
##  <a name="setthreadpriority"></a>  CWinThread::SetThreadPriority  
 Cette fonction définit le niveau de priorité du thread actuel dans sa classe de priorité.  
  
```  
BOOL SetThreadPriority(int nPriority);
```  
  
### <a name="parameters"></a>Paramètres  
 `nPriority`  
 Spécifie le nouveau niveau de priorité de thread dans sa classe de priorité. Ce paramètre doit être une des valeurs suivantes, répertoriées à partir de la priorité la plus élevée à la plus faible :  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **NIVEAU DE PRIORITÉ**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Pour plus d’informations sur ces priorités, consultez [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) dans le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Il peut uniquement être appelée après [CreateThread](#createthread) retourne avec succès.  
  
##  <a name="suspendthread"></a>  CWinThread::SuspendThread  
 Incrémente en cours de suspension du thread count.  
  
```  
DWORD SuspendThread();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le thread du précédent suspendre le nombre de cas de réussite ; `0xFFFFFFFF` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Si n’importe quel thread possède un compteur de suspension supérieur à zéro, ce thread ne s’exécute pas. Le thread peut être repris en appelant le [ResumeThread](#resumethread) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CWinApp (classe)](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
