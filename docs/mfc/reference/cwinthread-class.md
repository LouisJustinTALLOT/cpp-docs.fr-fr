---
title: Classe CWinThread
ms.date: 11/04/2016
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
ms.openlocfilehash: f2e95dd3ba8be31633590e37d95dedc8749ebdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367418"
---
# <a name="cwinthread-class"></a>Classe CWinThread

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
|[CWinThread::CreateThread](#createthread)|Commence l’exécution d’un `CWinThread` objet.|
|[CWinThread::ExitInstance](#exitinstance)|Remplacer pour nettoyer lorsque votre thread se termine.|
|[CWinThread::GetMainWnd](#getmainwnd)|Récupère un pointeur vers la fenêtre principale pour le thread.|
|[CWinThread::GetThreadPriority](#getthreadpriority)|Obtient la priorité du fil actuel.|
|[CWinThread::InitInstance](#initinstance)|Remplacement pour effectuer l’initialisation d’instance de fil.|
|[CWinThread::IsIdleMessage](#isidlemessage)|Vérifie les messages spéciaux.|
|[CWinThread::OnIdle](#onidle)|Remplacer pour effectuer un traitement de temps de ralenti spécifique au fil.|
|[CWinThread::PostThreadMessage](#postthreadmessage)|Affiche un message `CWinThread` à un autre objet.|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtre les messages avant d’être envoyés aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Intercepte certains messages avant qu’ils n’atteignent l’application.|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Intercepte toutes les exceptions non gérées lancées par le message et les gestionnaires de commande du thread.|
|[CWinThread::PumpMessage](#pumpmessage)|Contient la boucle de message du thread.|
|[CWinThread::ResumeThread](#resumethread)|Décréments le compte de suspension d’un thread.|
|[CWinThread::Run](#run)|Fonction de contrôle des threads avec une pompe à messages. Remplacement pour personnaliser la boucle de message par défaut.|
|[CWinThread::SetThreadPriority](#setthreadpriority)|Définit la priorité du thread actuel.|
|[CWinThread::SuspendThread](#suspendthread)|Incréments le compte de suspension d’un thread.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CWinThread::opérateur HANDLE](#operator_handle)|Récupère la poignée `CWinThread` de l’objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Précise s’il faut détruire l’objet à la terminaison du thread.|
|[CWinThread::m_hThread](#m_hthread)|Gérer le thread actuel.|
|[CWinThread::m_nThreadID](#m_nthreadid)|ID du fil actuel.|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Pointeur vers la fenêtre principale de l’application de conteneur lorsqu’un serveur OLE est actif.|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Tient un pointeur sur la fenêtre principale de l’application.|

## <a name="remarks"></a>Notes

Le fil conducteur de l’exécution est `CWinApp`généralement fourni par un objet dérivé de ; `CWinApp` est dérivé `CWinThread`de . Des `CWinThread` objets supplémentaires permettent plusieurs threads dans une application donnée.

Il existe deux types généraux `CWinThread` de threads qui prennent en charge : les fils de travailleur et les threads d’interface utilisateur. Les fils des travailleurs n’ont pas de pompe de message : par exemple, un thread qui effectue des calculs d’arrière-plan dans une application de feuille de calcul. Les threads d’interface utilisateur ont une pompe de message et des messages de processus reçus du système. [CWinApp](../../mfc/reference/cwinapp-class.md) et les classes qui en découlent sont des exemples de threads utilisateur-interface. D’autres threads d’interface utilisateur `CWinThread`peuvent également être dérivés directement de .

Les objets `CWinThread` de classe existent généralement pour la durée du fil. Si vous souhaitez modifier ce comportement, [définissez m_bAutoDelete](#m_bautodelete) à FALSE.

La `CWinThread` classe est nécessaire pour rendre votre code et MFC entièrement en sécurité. Les données thread-locales utilisées par le cadre `CWinThread` pour maintenir des informations spécifiques au thread sont gérées par des objets. En raison de `CWinThread` cette dépendance à gérer les données thread-local, tout thread qui utilise MFC doit être créé par MFC. Par exemple, un thread créé par la fonction de temps d’exécution [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) ne peut pas utiliser d’API MFC.

Pour créer un thread, appelez [AfxBeginThread](application-information-and-management.md#afxbeginthread). Il existe deux formulaires, selon que vous voulez un travailleur ou un thread utilisateur-interface. Si vous voulez un thread utilisateur-interface, passez à `AfxBeginThread` un pointeur à la `CRuntimeClass` de votre `CWinThread`classe dérivée. Si vous souhaitez créer un thread `AfxBeginThread` de travailleur, passez à un pointeur à la fonction de contrôle et au paramètre de la fonction de contrôle. Pour les fils de travail et les threads d’interface utilisateur, vous pouvez spécifier des paramètres facultatifs qui modifient la priorité, la taille de la pile, les drapeaux de création et les attributs de sécurité. `AfxBeginThread`retournera un pointeur `CWinThread` sur votre nouvel objet.

Au lieu `AfxBeginThread`d’appeler, `CWinThread`vous pouvez construire `CreateThread`un objet dérivé, puis appeler . Cette méthode de construction en deux étapes est `CWinThread` utile si vous souhaitez réutiliser l’objet entre la création successive et les interruptions d’exécutions de threads.

Pour plus `CWinThread`d’informations sur , voir les articles [Multithreading avec C et MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: Creating User-Interface Threads](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: Creating Worker Threads](../../parallel/multithreading-creating-worker-threads.md), et [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread::CreateThread

Crée un thread à exécuter dans l’espace d’adresse du processus d’appel.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Paramètres

*dwCreateFlags dwCreateFlags dwCreateFlags dw*<br/>
Spécifie un drapeau supplémentaire qui contrôle la création du fil. Ce drapeau peut contenir l’une des deux valeurs :

- CREATE_SUSPENDED Démarrer le fil avec un compte de suspension d’un. Utilisez CREATE_SUSPENDED si vous souhaitez parasminer les `CWinThread` données des membres de l’objet, telles que [m_bAutoDelete](#m_bautodelete) ou tout membre de votre classe dérivée, avant que le thread ne commence à fonctionner. Une fois votre initialisation terminée, utilisez le [CWinThread::ResumeThread](#resumethread) pour démarrer le thread en cours d’exécution. Le thread ne `CWinThread::ResumeThread` s’exécutera pas tant qu’il n’est pas appelé.

- **0** Démarrer le fil immédiatement après la création.

*nStackSize (en)*<br/>
Specifie la taille des octets de la pile pour le nouveau fil. Si **0**, la taille de la pile par défaut à la même taille que celle du fil principal du processus.

*lpSecurityAttrs*<br/>
Indique une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie les attributs de sécurité pour le thread.

### <a name="return-value"></a>Valeur de retour

Nonzero si le fil est créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Utilisez `AfxBeginThread` pour créer un objet de fil et l’exécuter en une seule étape. Utilisez `CreateThread` si vous souhaitez réutiliser l’objet de fil entre la création successive et la fin des exécutions de thread.

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread::CWinThread

Construit un objet `CWinThread`.

```
CWinThread();
```

### <a name="remarks"></a>Notes

Pour commencer l’exécution du thread, appelez la fonction membre [CreateThread.](#createthread) Vous allez généralement créer des threads en appelant [AfxBeginThread](application-information-and-management.md#afxbeginthread), qui appellera ce constructeur et `CreateThread`.

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread::ExitInstance

Appelé par le cadre de l’intérieur d’une fonction membre [course](#run) rarement annulée de quitter cette instance du fil, ou si un appel à [InitInstance](#initinstance) échoue.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Valeur de retour

Code de sortie du fil; 0 n’indique aucune erreur, et les valeurs supérieures à 0 indiquent une erreur. Cette valeur peut être récupérée en appelant [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Notes

N’appelez pas cette fonction de `Run` membre de n’importe où, mais dans la fonction de membre. Cette fonction de membre n’est utilisée que dans les threads utilisateur-interface.

La mise en œuvre `CWinThread` par défaut de cette fonction supprime l’objet si [m_bAutoDelete](#m_bautodelete) est VRAI. Remplacez cette fonction si vous souhaitez effectuer un nettoyage supplémentaire lorsque votre thread se termine. Votre implémentation de `ExitInstance` devrait appeler la version de la classe de base après l’exécution de votre code.

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread::GetMainWnd

Si votre application est un serveur OLE, appelez cette fonction pour récupérer un pointeur `m_pMainWnd` vers la fenêtre principale active de l’application au lieu de se référer directement au membre de l’objet d’application.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Valeur de retour

Cette fonction renvoie un pointeur à l’un des deux types de fenêtres. Si votre thread fait partie d’un serveur OLE et dispose d’un objet actif à l’intérieur d’un conteneur `CWinThread` actif, cette fonction renvoie le [CWinApp : m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) membre des données de l’objet.

S’il n’y a pas d’objet actif dans un conteneur ou si votre application n’est pas un serveur OLE, cette fonction renvoie [le](#m_pmainwnd) m_pMainWnd membre des données de votre objet de thread.

### <a name="remarks"></a>Notes

Pour les threads utilisateur-interface, cela équivaut à se référer directement au `m_pActiveWnd` membre de votre objet d’application.

Si votre application n’est pas un serveur OLE, l’appel de cette fonction équivaut à se référer directement au `m_pMainWnd` membre de votre objet d’application.

Remplacer cette fonction pour modifier le comportement par défaut.

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread::GetThreadPriority

Obtient le niveau actuel de priorité de thread de ce thread.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Valeur de retour

Le niveau actuel de priorité de thread au sein de sa classe de priorité. La valeur retournée sera l’une des suivantes, énumérée de la plus haute priorité au plus bas :

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Pour plus d’informations sur ces priorités, voir [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread::InitInstance

`InitInstance`doivent être remplacés pour initialiser chaque nouvelle instance d’un thread utilisateur-interface.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation est réussie; sinon 0.

### <a name="remarks"></a>Notes

En règle générale, vous remplacez `InitInstance` pour effectuer des tâches qui doivent être accomplies lorsqu’un thread est créé pour la première fois.

Cette fonction de membre n’est utilisée que dans les threads utilisateur-interface. Effectuer la initialisation des fils de travailleur dans la fonction de contrôle passé à [AfxBeginThread](application-information-and-management.md#afxbeginthread).

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread::IsIdleMessage

Remplacez cette fonction `OnIdle` pour éviter d’être appelé après la génération de messages spécifiques.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Indique le message en cours de traitement.

### <a name="return-value"></a>Valeur de retour

Nonzero `OnIdle` si doit être appelé après le traitement du message; sinon 0.

### <a name="remarks"></a>Notes

L’implémentation `OnIdle` par défaut n’appelle pas après les messages et les messages de souris redondants générés par des carets clignotants.

Si une application a créé `OnIdle` une minuterie courte, sera appelé fréquemment, causant des problèmes de performance. Pour améliorer les performances d’une `IsIdleMessage` telle application, `CWinApp`remplacez la classe dérivée de l’application pour vérifier s’il WM_TIMER messages comme suit :

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

La manipulation de WM_TIMER de cette façon améliorera les performances des applications qui utilisent des minuteries courtes.

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread::m_bAutoDelete

Précise si l’objet doit être automatiquement supprimé lors de la `CWinThread` terminaison du thread.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Notes

Le `m_bAutoDelete` membre des données est une variable publique de type BOOL.

La valeur `m_bAutoDelete` de n’affecte pas la façon dont la poignée de thread sous-jacente est fermée, mais il affecte le moment de la fermeture de la poignée. La poignée de fil `CWinThread` est toujours fermée lorsque l’objet est détruit.

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread::m_hThread

Poignée au fil attaché `CWinThread`à ceci .

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Notes

Le `m_hThread` membre des données est une variable publique de type HANDLE. Il n’est valable que si l’objet sous-jacent de fil de noyau existe actuellement, et le manche n’a pas encore été fermé.

Le destructeur CWinThread appelle CloseHandle sur `m_hThread`. Si [m_bAutoDelete](#m_bautodelete) est VRAI lorsque le thread se termine, l’objet CWinThread est détruit, ce qui invalide tous les indications de l’objet CWinThread et de ses variables membres. Vous devrez `m_hThread` peut-être le membre vérifier la valeur de sortie de thread ou attendre un signal. Pour garder l’objet CWinThread et son `m_hThread` membre pendant `m_bAutoDelete` l’exécution du fil et après qu’il se termine, réglé à FALSE avant de permettre l’exécution du fil de continuer. Sinon, le thread peut se terminer, détruire l’objet CWinThread, et fermer la poignée avant d’essayer de l’utiliser. Si vous utilisez cette technique, vous êtes responsable de la suppression de l’objet CWinThread.

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread::m_nThreadID

ID du fil attaché `CWinThread`à ce .

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Notes

Le `m_nThreadID` membre des données est une variable publique de type DWORD. Il n’est valable que si l’objet sous-jacent de fil de noyau existe actuellement.
Voir aussi des remarques sur [m_hThread](#m_hthread) vie.

### <a name="example"></a>Exemple

  Voir l’exemple pour [AfxGetThread](application-information-and-management.md#afxgetthread).

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd

Utilisez ce membre de données pour stocker un pointeur sur l’objet de fenêtre actif de votre thread.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Notes

La bibliothèque de classe Microsoft Foundation mettra automatiquement fin `m_pActiveWnd` à votre thread lorsque la fenêtre mentionnée par est fermée. Si ce thread est le fil principal pour une application, l’application sera également terminée. Si ce membre de données est NULL, `CWinApp` la fenêtre active pour l’objet de l’application sera héritée. `m_pActiveWnd`est une variable `CWnd*`publique de type .

En règle générale, vous définissez `InitInstance`cette variable de membre lorsque vous l’emportez . Dans un thread de travailleur, la valeur de ce membre de données est héritée de son fil parent.

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread::m_pMainWnd

Utilisez ce membre de données pour stocker un pointeur sur l’objet principal de la fenêtre de votre thread.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Notes

La bibliothèque de classe Microsoft Foundation mettra automatiquement fin `m_pMainWnd` à votre thread lorsque la fenêtre mentionnée par est fermée. Si ce thread est le fil principal pour une application, l’application sera également terminée. Si ce membre de données est NULL, `CWinApp` la fenêtre principale de l’objet de l’application sera utilisée pour déterminer quand mettre fin au thread. `m_pMainWnd`est une variable `CWnd*`publique de type .

En règle générale, vous définissez `InitInstance`cette variable de membre lorsque vous l’emportez . Dans un thread de travailleur, la valeur de ce membre de données est héritée de son fil parent.

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CWinThread::OnIdle

Remplacer cette fonction de membre pour effectuer un traitement au ralenti.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Paramètres

*lCompte*<br/>
Un compteur incrémenté `OnIdle` à chaque fois est appelé lorsque la file d’attente de message du fil est vide. Ce nombre est réinitialisé à 0 chaque fois qu’un nouveau message est traité. Vous pouvez utiliser le *paramètre lCount* pour déterminer la durée relative pendant laquelle le thread a été inactif sans traiter un message.

### <a name="return-value"></a>Valeur de retour

Nonzero pour recevoir plus de temps de traitement au ralenti; 0 si plus de temps de traitement au ralenti n’est pas nécessaire.

### <a name="remarks"></a>Notes

`OnIdle`est appelé dans la boucle de message par défaut lorsque la file d’attente du thread est vide. Utilisez votre remplacement pour appeler vos propres tâches de contrôle de ralenti.

`OnIdle`devrait retourner 0 pour indiquer qu’aucun délai supplémentaire de traitement au ralenti n’est nécessaire. Le *paramètre lCount* est incrémenté chaque fois `OnIdle` que la file d’attente est vide et est réinitialisé à 0 chaque fois qu’un nouveau message est traité. Vous pouvez appeler vos différentes routines de ralenti en fonction de ce compte.

La mise en œuvre par défaut de cette fonction membre libère des objets temporaires et des bibliothèques de liaison dynamique inutilisées de la mémoire.

Cette fonction de membre n’est utilisée que dans les threads utilisateur-interface.

Étant donné que l’application ne peut pas traiter les messages avant `OnIdle` les retours, ne effectuez pas de longues tâches dans cette fonction.

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread::opérateur HANDLE

Récupère la poignée `CWinThread` de l’objet.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, la poignée de l’objet de fil; autrement, NULL.

### <a name="remarks"></a>Notes

Utilisez la poignée pour appeler directement les API Windows.

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::PostThreadMessage

Appelé pour poster un message `CWinThread` défini par l’utilisateur à un autre objet.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*Message*<br/>
ID du message défini par l’utilisateur.

*wParam*<br/>
Premier paramètre de message.

*lParam*<br/>
Deuxième paramètre de message.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le message posté est cartographié sur le gestionnaire de message approprié par la carte de message macro ON_THREAD_MESSAGE.

> [!NOTE]
> Lorsque vous appelez [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew), le message est placé dans la file d’attente du message du thread. Cependant, comme les messages affichés de cette façon ne sont pas associés à une fenêtre, MFC ne les enverra pas aux gestionnaires de messages ou de commande. Afin de gérer ces messages, `PreTranslateMessage()` remplacez la fonction de votre classe dérivée de CWinApp et manipulez les messages manuellement.

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage

Remplacer cette fonction pour filtrer les messages de fenêtre avant qu’ils ne soient envoyés aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Indique une [structure MSG](/windows/win32/api/winuser/ns-winuser-msg) contenant le message à traiter.

### <a name="return-value"></a>Valeur de retour

Nonzero si le message `PreTranslateMessage` a été entièrement traité et ne doit pas être traité plus loin. Zéro si le message doit être traité de la manière normale.

### <a name="remarks"></a>Notes

Cette fonction de membre n’est utilisée que dans les threads utilisateur-interface.

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter

La fonction de crochet du cadre appelle cette fonction de membre pour filtrer et répondre à certains messages Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*Code*<br/>
Spécifie un code de crochet. Cette fonction membre utilise le code pour déterminer comment traiter *lpMsg.*

*lpMsg*<br/>
Un pointeur vers une [structure Windows MSG](/windows/win32/api/winuser/ns-winuser-msg).

### <a name="return-value"></a>Valeur de retour

Nonzero si le message est traité; sinon 0.

### <a name="remarks"></a>Notes

Une fonction de crochet traite les événements avant qu’ils ne soient envoyés au traitement normal du message de l’application.

Si vous remplacez cette fonctionnalité avancée, assurez-vous d’appeler la version de base pour maintenir le traitement du crochet du cadre.

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::ProcessWndProcException

Le cadre appelle cette fonction de membre chaque fois que le gestionnaire n’attrape pas une exception jetée dans l’un des messages ou des gestionnaires de commande de votre thread.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*E*<br/>
Indique une exception non gérée.

*pMsg*<br/>
Indique une [structure MSG](/windows/win32/api/winuser/ns-winuser-msg) contenant des informations sur le message Windows qui a causé le cadre de jeter une exception.

### <a name="return-value"></a>Valeur de retour

-1 si une exception WM_CREATE est générée; sinon 0.

### <a name="remarks"></a>Notes

N’appelez pas directement cette fonction de membre.

La mise en œuvre par défaut de cette fonction membre ne gère que les exceptions générées par les messages suivants :

|Commande|Action|
|-------------|------------|
|WM_CREATE|Échouer.|
|WM_PAINT|Validez la fenêtre affectée, empêchant ainsi la génération d’un autre message WM_PAINT.|

Remplacez cette fonction de membre pour assurer la gestion globale de vos exceptions. Appelez la fonctionnalité de base uniquement si vous souhaitez afficher le comportement par défaut.

Cette fonction de membre n’est utilisée que dans les threads qui ont une pompe de message.

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::PumpMessage

Contient la boucle de message du thread.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Notes

`PumpMessage`contient la boucle de message du thread. `PumpMessage`est appelé `CWinThread` par pour pomper les messages du thread. Vous pouvez `PumpMessage` appeler directement pour forcer le traitement `PumpMessage` des messages, ou vous pouvez passer outre pour modifier son comportement par défaut.

L’appel `PumpMessage` directement et l’avant de son comportement par défaut est recommandé pour les utilisateurs avancés seulement.

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread::ResumeThread

Appelé à reprendre l’exécution d’un fil qui a été suspendu par la fonction du membre [SuspendThread,](#suspendthread) ou d’un fil créé avec le drapeau CREATE_SUSPENDED.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Valeur de retour

Le compte de suspension précédent du fil en cas de succès; `0xFFFFFFFF` autrement. Si la valeur de retour est nulle, le thread actuel n’a pas été suspendu. Si la valeur de retour est une, le thread a été suspendu, mais est maintenant redémarré. Toute valeur de retour supérieure à la première signifie que le thread reste suspendu.

### <a name="remarks"></a>Notes

Le compte de suspension du thread actuel est réduit d’un. Si le nombre de suspensions est réduit à zéro, le fil reprend l’exécution; sinon le fil reste suspendu.

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread::Run

Fournit une boucle de message par défaut pour les threads d’interface utilisateur.

```
virtual int Run();
```

### <a name="return-value"></a>Valeur de retour

Une valeur **int** qui est retournée par le fil. Cette valeur peut être récupérée en appelant [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Notes

`Run`acquiert et envoie des messages Windows jusqu’à ce que l’application reçoive un [message WM_QUIT.](/windows/win32/winmsg/wm-quit) Si la file d’attente de `Run` message `OnIdle` du thread ne contient actuellement aucun message, les appels pour effectuer un traitement en temps de marche. Les messages entrants vont à la fonction [membre PreTranslateMessage](#pretranslatemessage) pour le traitement spécial, puis à la fonction Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) pour la traduction standard du clavier. Enfin, la fonction [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows s’appelle.

`Run`est rarement remplacé, mais vous pouvez l’emporter pour mettre en œuvre un comportement spécial.

Cette fonction de membre n’est utilisée que dans les threads utilisateur-interface.

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread::SetThreadPriority

Cette fonction définit le niveau prioritaire du thread actuel au sein de sa classe de priorité.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Paramètres

*nPriorité*<br/>
Spécifie le nouveau niveau de priorité de thread au sein de sa classe de priorité. Ce paramètre doit être l’une des valeurs suivantes, énumérés de la plus haute priorité au plus bas :

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Pour plus d’informations sur ces priorités, voir [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Il ne peut être appelé qu’après les retours réussis [de CreateThread.](#createthread)

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread::SuspendThread

Incréments le compte de suspension du thread actuel.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Valeur de retour

Le compte de suspension précédent du fil en cas de succès; `0xFFFFFFFF` autrement.

### <a name="remarks"></a>Notes

Si un thread a un compte de suspension au-dessus de zéro, ce thread ne s’exécute pas. Le thread peut être repris en appelant la fonction de membre [ResumeThread.](#resumethread)

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWinApp, classe](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
