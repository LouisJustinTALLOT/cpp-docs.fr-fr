---
description: 'En savoir plus sur : classe CWinThread'
title: CWinThread (classe)
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
ms.openlocfilehash: f9f89aa6397f44c95e8958d077fe18258e3c17f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342606"
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
|[CWinThread :: CWinThread](#cwinthread)|Construit un objet `CWinThread`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinThread :: CreateThread](#createthread)|Démarre l’exécution d’un `CWinThread` objet.|
|[CWinThread :: ExitInstance](#exitinstance)|Substituez pour nettoyer quand votre thread s’arrête.|
|[CWinThread :: GetMainWnd](#getmainwnd)|Récupère un pointeur vers la fenêtre principale pour le thread.|
|[CWinThread :: GetThreadPriority](#getthreadpriority)|Obtient la priorité du thread actuel.|
|[CWinThread :: InitInstance](#initinstance)|Substituez pour effectuer l’initialisation de l’instance de thread.|
|[CWinThread :: IsIdleMessage](#isidlemessage)|Recherche des messages spéciaux.|
|[CWinThread :: OnIdle](#onidle)|Substituez pour effectuer un traitement du temps d’inactivité spécifique au thread.|
|[CWinThread ::P ostThreadMessage](#postthreadmessage)|Publie un message dans un autre `CWinThread` objet.|
|[CWinThread ::P reTranslateMessage](#pretranslatemessage)|Filtre les messages avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread ::P rocessMessageFilter](#processmessagefilter)|Intercepte certains messages avant qu’ils n’atteignent l’application.|
|[CWinThread ::P rocessWndProcException](#processwndprocexception)|Intercepte toutes les exceptions non gérées levées par les gestionnaires de commandes et de messages du thread.|
|[CWinThread ::P umpMessage](#pumpmessage)|Contient la boucle de message du thread.|
|[CWinThread :: ResumeThread](#resumethread)|Décrémente le nombre de suspensions d’un thread.|
|[CWinThread :: Run](#run)|Contrôle de la fonction pour les threads avec une pompe de messages. Substituez pour personnaliser la boucle de message par défaut.|
|[CWinThread :: SetThreadPriority](#setthreadpriority)|Définit la priorité du thread actuel.|
|[CWinThread :: SuspendThread](#suspendthread)|Incrémente le nombre de suspensions d’un thread.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CWinThread :: Operator, HANDLE](#operator_handle)|Récupère le handle de l' `CWinThread` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CWinThread :: m_bAutoDelete](#m_bautodelete)|Spécifie s’il faut détruire l’objet au moment de l’arrêt du thread.|
|[CWinThread :: m_hThread](#m_hthread)|Handle vers le thread actuel.|
|[CWinThread :: m_nThreadID](#m_nthreadid)|ID du thread actuel.|
|[CWinThread :: m_pActiveWnd](#m_pactivewnd)|Pointeur vers la fenêtre principale de l’application conteneur lorsqu’un serveur OLE est actif sur place.|
|[CWinThread :: m_pMainWnd](#m_pmainwnd)|Contient un pointeur vers la fenêtre principale de l’application.|

## <a name="remarks"></a>Notes

Le thread principal d’exécution est généralement fourni par un objet dérivé de `CWinApp` ; `CWinApp` est dérivé de `CWinThread` . Les `CWinThread` objets supplémentaires autorisent plusieurs threads dans une application donnée.

Il existe deux types généraux de threads qui `CWinThread` prennent en charge : les threads de travail et les threads d’interface utilisateur. Les threads de travail n’ont pas de pompe de messages : par exemple, un thread qui effectue des calculs en arrière-plan dans une application de feuille de calcul. Les threads d’interface utilisateur ont une pompe de messages et traitent les messages reçus du système. Les classes [CWinApp](../../mfc/reference/cwinapp-class.md) et dérivées de cette classe sont des exemples de threads de l’interface utilisateur. D’autres threads de l’interface utilisateur peuvent également être dérivés directement à partir de `CWinThread` .

Les objets de la classe `CWinThread` existent généralement pour la durée du thread. Si vous souhaitez modifier ce comportement, affectez à [m_bAutoDelete](#m_bautodelete) la valeur false.

La `CWinThread` classe est nécessaire pour rendre votre code et MFC entièrement thread-safe. Les données locales de thread utilisées par l’infrastructure pour conserver les informations spécifiques au thread sont gérées par les `CWinThread` objets. En raison de cette dépendance `CWinThread` à la gestion des données locales de thread, tout thread qui utilise MFC doit être créé par MFC. Par exemple, un thread créé par la fonction runtime [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) ne peut pas utiliser d’API MFC.

Pour créer un thread, appelez [AfxBeginThread](application-information-and-management.md#afxbeginthread). Il existe deux formes, selon que vous voulez un thread de travail ou un thread d’interface utilisateur. Si vous souhaitez un thread d’interface utilisateur, transmettez à `AfxBeginThread` un pointeur désignant le `CRuntimeClass` de votre `CWinThread` classe dérivée de. Si vous souhaitez créer un thread de travail, transmettez à `AfxBeginThread` un pointeur vers la fonction de contrôle et le paramètre à la fonction de contrôle. Pour les threads de travail et les threads d’interface utilisateur, vous pouvez spécifier des paramètres facultatifs qui modifient la priorité, la taille de la pile, les indicateurs de création et les attributs de sécurité. `AfxBeginThread` retourne un pointeur vers votre nouvel `CWinThread` objet.

Au lieu d’appeler `AfxBeginThread` , vous pouvez construire un objet dérivé de, puis `CWinThread` appeler `CreateThread` . Cette méthode de construction en deux étapes est utile si vous souhaitez réutiliser l' `CWinThread` objet entre une création et des arrêts successifs des exécutions de threads.

Pour plus d’informations sur `CWinThread` , consultez les articles sur le [Multithreading avec C++ et MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading : création de threads User-Interface](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading : création de threads de travail](../../parallel/multithreading-creating-worker-threads.md)et [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a> CWinThread :: CreateThread

Crée un thread à exécuter dans l’espace d’adressage du processus appelant.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Paramètres

*dwCreateFlags*<br/>
Spécifie un indicateur supplémentaire qui contrôle la création du thread. Cet indicateur peut contenir l’une des deux valeurs suivantes :

- CREATE_SUSPENDED démarrer le thread avec un nombre de suspension d’un. Utilisez CREATE_SUSPENDED si vous souhaitez initialiser toutes les données de membre de l' `CWinThread` objet, telles que [m_bAutoDelete](#m_bautodelete) ou les membres de votre classe dérivée, avant que le thread ne commence à s’exécuter. Une fois l’initialisation terminée, utilisez [CWinThread :: ResumeThread](#resumethread) pour démarrer le thread en cours d’exécution. Le thread ne s’exécute pas tant que `CWinThread::ResumeThread` n’est pas appelé.

- **0** démarre le thread immédiatement après la création.

*nStackSize*<br/>
Spécifie la taille en octets de la pile pour le nouveau thread. Si la **valeur est 0**, la taille de la pile est par défaut de la même taille que celle du thread principal du processus.

*lpSecurityAttrs*<br/>
Pointe vers une structure de [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie les attributs de sécurité du thread.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le thread est créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `AfxBeginThread` pour créer un objet thread et l’exécuter en une seule étape. Utilisez `CreateThread` si vous souhaitez réutiliser l’objet thread entre une création et un arrêt successifs des exécutions de thread.

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a> CWinThread :: CWinThread

Construit un objet `CWinThread`.

```
CWinThread();
```

### <a name="remarks"></a>Notes

Pour commencer l’exécution du thread, appelez la fonction membre [CreateThread](#createthread) . Vous allez généralement créer des threads en appelant [AfxBeginThread](application-information-and-management.md#afxbeginthread), qui appellera ce constructeur et `CreateThread` .

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a> CWinThread :: ExitInstance

Appelée par l’infrastructure à partir d’une fonction membre d' [exécution](#run) rarement remplacée pour quitter cette instance du thread, ou si un appel à [InitInstance](#initinstance) échoue.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Valeur renvoyée

Code de sortie du thread ; 0 indique l’absence d’erreurs, et les valeurs supérieures à 0 indiquent une erreur. Cette valeur peut être récupérée en appelant [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Notes

N’appelez pas cette fonction membre à partir de n’importe où, mais dans la `Run` fonction membre. Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur.

L’implémentation par défaut de cette fonction supprime l' `CWinThread` objet si [m_bAutoDelete](#m_bautodelete) a la valeur true. Substituez cette fonction si vous souhaitez effectuer un nettoyage supplémentaire lorsque votre thread se termine. Votre implémentation de `ExitInstance` doit appeler la version de la classe de base après l’exécution de votre code.

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a> CWinThread :: GetMainWnd

Si votre application est un serveur OLE, appelez cette fonction pour récupérer un pointeur vers la fenêtre principale active de l’application au lieu de faire directement référence au `m_pMainWnd` membre de l’objet d’application.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Valeur renvoyée

Cette fonction retourne un pointeur vers l’un des deux types de fenêtres. Si votre thread fait partie d’un serveur OLE et possède un objet qui est actif sur place à l’intérieur d’un conteneur actif, cette fonction retourne le membre de données [CWinApp :: m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) de l' `CWinThread` objet.

Si aucun objet n’est actif sur place dans un conteneur ou si votre application n’est pas un serveur OLE, cette fonction retourne le [m_pMainWnd](#m_pmainwnd) données membres de votre objet thread.

### <a name="remarks"></a>Notes

Pour les threads d’interface utilisateur, cela équivaut à faire directement référence au `m_pActiveWnd` membre de votre objet application.

Si votre application n’est pas un serveur OLE, l’appel de cette fonction équivaut à faire directement référence au `m_pMainWnd` membre de votre objet application.

Substituez cette fonction pour modifier le comportement par défaut.

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a> CWinThread :: GetThreadPriority

Obtient le niveau de priorité de thread actuel de ce thread.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Valeur renvoyée

Niveau de priorité actuel du thread dans sa classe de priorité. La valeur retournée sera l’une des valeurs suivantes, de la plus haute à la plus faible :

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Pour plus d’informations sur ces priorités, consultez [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a> CWinThread :: InitInstance

`InitInstance` doit être substitué pour initialiser chaque nouvelle instance d’un thread d’interface utilisateur.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si l’initialisation réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

En général, vous remplacez `InitInstance` pour effectuer des tâches qui doivent être terminées lors de la création d’un thread.

Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur. Exécuter l’initialisation des threads de travail dans la fonction de contrôle passée à [AfxBeginThread](application-information-and-management.md#afxbeginthread).

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a> CWinThread :: IsIdleMessage

Substituez cette fonction pour empêcher l' `OnIdle` appel après la génération de messages spécifiques.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Pointe vers le message en cours de traitement.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si `OnIdle` doit être appelé après le traitement du message ; sinon, 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut n’appelle pas `OnIdle` après des messages de souris redondants et des messages générés par des signes de clignotement.

Si une application a créé un minuteur bref, `OnIdle` est appelé fréquemment, ce qui entraîne des problèmes de performances. Pour améliorer les performances d’une application de ce type, remplacez `IsIdleMessage` dans la `CWinApp` classe dérivée de l’application pour rechercher les messages WM_TIMER comme suit :

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

La gestion de WM_TIMER de cette manière améliore les performances des applications qui utilisent des minuteurs courts.

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a> CWinThread :: m_bAutoDelete

Spécifie si l' `CWinThread` objet doit être automatiquement supprimé au moment de l’arrêt du thread.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Notes

Le `m_bAutoDelete` membre de données est une variable publique de type bool.

La valeur de `m_bAutoDelete` n’affecte pas la manière dont le handle de thread sous-jacent est fermé, mais elle affecte le minutage de la fermeture du handle. Le handle de thread est toujours fermé lorsque l' `CWinThread` objet est détruit.

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a> CWinThread :: m_hThread

Handle vers le thread attaché à ce `CWinThread` .

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Notes

Le `m_hThread` membre de données est une variable publique de type handle. Elle est valide uniquement si l’objet de thread de noyau sous-jacent existe actuellement, et si le handle n’a pas encore été fermé.

Le destructeur CWinThread appelle CloseHandle sur `m_hThread` . Si [m_bAutoDelete](#m_bautodelete) a la valeur true lorsque le thread se termine, l’objet CWinThread est détruit, ce qui invalide tous les pointeurs vers l’objet CWinThread et ses variables membres. Vous aurez peut-être besoin du `m_hThread` membre pour vérifier la valeur de sortie du thread ou pour attendre un signal. Pour conserver l’objet CWinThread et son `m_hThread` membre pendant l’exécution du thread et après son arrêt, affectez à la valeur `m_bAutoDelete` false avant d’autoriser l’exécution du thread à continuer. Sinon, le thread peut se terminer, détruire l’objet CWinThread et fermer le descripteur avant d’essayer de l’utiliser. Si vous utilisez cette technique, vous êtes responsable de la suppression de l’objet CWinThread.

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a> CWinThread :: m_nThreadID

ID du thread attaché à ce `CWinThread` .

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Notes

Le `m_nThreadID` membre de données est une variable publique de type DWORD. Elle est valide uniquement si l’objet de thread de noyau sous-jacent existe actuellement.
Consultez également les notes relatives à [m_hThread](#m_hthread) durée de vie.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [AfxGetThread](application-information-and-management.md#afxgetthread).

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a> CWinThread :: m_pActiveWnd

Utilisez ce membre de données pour stocker un pointeur vers l’objet de fenêtre active de votre thread.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Notes

Le bibliothèque MFC (Microsoft Foundation Class) met automatiquement fin à votre thread lorsque la fenêtre référencée par `m_pActiveWnd` est fermée. Si ce thread est le thread principal d’une application, l’application s’arrête également. Si ce membre de données a la valeur NULL, la fenêtre active de l’objet de l’application est `CWinApp` héritée. `m_pActiveWnd` variable publique de type `CWnd*` .

En général, vous définissez cette variable membre lorsque vous substituez `InitInstance` . Dans un thread de travail, la valeur de ce membre de données est héritée de son thread parent.

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a> CWinThread :: m_pMainWnd

Utilisez ce membre de données pour stocker un pointeur vers l’objet de fenêtre principale de votre thread.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Notes

Le bibliothèque MFC (Microsoft Foundation Class) met automatiquement fin à votre thread lorsque la fenêtre référencée par `m_pMainWnd` est fermée. Si ce thread est le thread principal d’une application, l’application s’arrête également. Si ce membre de données a la valeur NULL, la fenêtre principale de l’objet de l’application `CWinApp` sera utilisée pour déterminer quand arrêter le thread. `m_pMainWnd` variable publique de type `CWnd*` .

En général, vous définissez cette variable membre lorsque vous substituez `InitInstance` . Dans un thread de travail, la valeur de ce membre de données est héritée de son thread parent.

## <a name="cwinthreadonidle"></a><a name="onidle"></a> CWinThread :: OnIdle

Substituez cette fonction membre pour effectuer un traitement en temps inactif.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Paramètres

*lCount*<br/>
Un compteur est incrémenté chaque fois `OnIdle` que la file d’attente de messages du thread est vide. Ce nombre est réinitialisé à 0 chaque fois qu’un nouveau message est traité. Vous pouvez utiliser le paramètre *lCount* pour déterminer la durée relative pendant laquelle le thread est inactif sans traiter un message.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro pour obtenir un temps de traitement plus inactif. 0 si aucun délai de traitement inactif n’est nécessaire.

### <a name="remarks"></a>Notes

`OnIdle` est appelé dans la boucle de messages par défaut lorsque la file d’attente de messages du thread est vide. Utilisez votre remplacement pour appeler vos propres tâches de gestionnaire d’inactivité en arrière-plan.

`OnIdle` doit retourner 0 pour indiquer qu’aucun temps de traitement inactif supplémentaire n’est nécessaire. Le paramètre *lCount* est incrémenté chaque fois `OnIdle` que est appelé lorsque la file d’attente de messages est vide et est réinitialisé à 0 à chaque fois qu’un nouveau message est traité. Vous pouvez appeler vos différentes routines inactives en fonction de ce nombre.

L’implémentation par défaut de cette fonction membre libère les objets temporaires et les bibliothèques de liens dynamiques inutilisées de la mémoire.

Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur.

Étant donné que l’application ne peut pas traiter les messages jusqu’à ce qu' `OnIdle` elle soit renvoyée, n’effectuez pas de tâches longues dans cette fonction.

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a> CWinThread :: Operator, HANDLE

Récupère le handle de l' `CWinThread` objet.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, handle de l’objet thread ; Sinon, NULL.

### <a name="remarks"></a>Notes

Utilisez le descripteur pour appeler directement des API Windows.

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a> CWinThread ::P ostThreadMessage

Appelé pour envoyer un message défini par l’utilisateur à un autre `CWinThread` objet.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*message*<br/>
ID du message défini par l’utilisateur.

*wParam*<br/>
Premier paramètre de message.

*lParam*<br/>
Deuxième paramètre de message.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le message publié est mappé au gestionnaire de messages approprié par la macro de la table des messages ON_THREAD_MESSAGE.

> [!NOTE]
> Lorsque vous appelez [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew), le message est placé dans la file d’attente de messages du thread. Toutefois, étant donné que les messages publiés de cette façon ne sont pas associés à une fenêtre, MFC ne les distribue pas aux gestionnaires de messages ou de commandes. Pour gérer ces messages, remplacez la `PreTranslateMessage()` fonction de votre classe dérivée de CWinApp et gérez les messages manuellement.

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a> CWinThread ::P reTranslateMessage

Remplacez cette fonction pour filtrer les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Pointe vers une [structure MSG](/windows/win32/api/winuser/ns-winuser-msg) contenant le message à traiter.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si le message a été entièrement traité dans `PreTranslateMessage` et ne doit pas être traité plus en détail. Zéro si le message doit être traité normalement.

### <a name="remarks"></a>Notes

Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur.

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a> CWinThread ::P rocessMessageFilter

La fonction de raccordement de l’infrastructure appelle cette fonction membre pour filtrer et répondre à certains messages Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*code*<br/>
Spécifie un code de raccordement. Cette fonction membre utilise le code pour déterminer comment traiter *lpMsg.*

*lpMsg*<br/>
Pointeur vers une [structure MSG](/windows/win32/api/winuser/ns-winuser-msg)Windows.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le message est traité ; Sinon, 0.

### <a name="remarks"></a>Notes

Une fonction de raccordement traite les événements avant leur envoi au traitement de message normal de l’application.

Si vous remplacez cette fonctionnalité avancée, veillez à appeler la version de classe de base pour gérer le processus de raccordement du Framework.

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a> CWinThread ::P rocessWndProcException

L’infrastructure appelle cette fonction membre chaque fois que le gestionnaire n’intercepte pas une exception levée dans l’un des gestionnaires de messages ou de commandes de votre thread.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*Envoyer*<br/>
Pointe vers une exception non gérée.

*pMsg*<br/>
Pointe vers une [structure MSG](/windows/win32/api/winuser/ns-winuser-msg) contenant des informations sur le message Windows à l’origine de la levée d’une exception par l’infrastructure.

### <a name="return-value"></a>Valeur renvoyée

-1 si une exception WM_CREATE est générée ; Sinon, 0.

### <a name="remarks"></a>Notes

N’appelez pas cette fonction membre directement.

L’implémentation par défaut de cette fonction membre gère uniquement les exceptions générées à partir des messages suivants :

|Commande|Action|
|-------------|------------|
|WM_CREATE|Incident.|
|WM_PAINT|Validez la fenêtre affectée, ce qui empêche la génération d’un autre message de WM_PAINT.|

Substituez cette fonction membre pour assurer le traitement global de vos exceptions. Appelez la fonctionnalité de base uniquement si vous souhaitez afficher le comportement par défaut.

Cette fonction membre est utilisée uniquement dans les threads qui ont une pompe de messages.

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a> CWinThread ::P umpMessage

Contient la boucle de message du thread.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Notes

`PumpMessage` contient la boucle de message du thread. `PumpMessage` est appelé par `CWinThread` pour pomper les messages du thread. Vous pouvez appeler `PumpMessage` directement pour forcer le traitement des messages, ou vous pouvez remplacer `PumpMessage` pour modifier son comportement par défaut.

`PumpMessage`L’appel direct et la substitution de son comportement par défaut sont recommandés pour les utilisateurs expérimentés uniquement.

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a> CWinThread :: ResumeThread

Appelé pour reprendre l’exécution d’un thread qui a été suspendu par la fonction membre [SuspendThread](#suspendthread) , ou un thread créé avec l’indicateur CREATE_SUSPENDED.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de suspensions précédentes du thread en cas de réussite ; `0xFFFFFFFF` sinon,. Si la valeur de retour est égale à zéro, le thread actuel n’a pas été suspendu. Si la valeur de retour est 1, le thread a été suspendu, mais est maintenant redémarré. Toute valeur de retour supérieure à un signifie que le thread reste suspendu.

### <a name="remarks"></a>Notes

Le nombre de suspensions du thread actuel est réduit d’une unité. Si le nombre de suspensions est réduit à zéro, le thread reprend l’exécution ; Sinon, le thread reste suspendu.

## <a name="cwinthreadrun"></a><a name="run"></a> CWinThread :: Run

Fournit une boucle de messages par défaut pour les threads d’interface utilisateur.

```
virtual int Run();
```

### <a name="return-value"></a>Valeur renvoyée

**`int`** Valeur retournée par le thread. Cette valeur peut être récupérée en appelant [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Notes

`Run` acquiert et distribue des messages Windows jusqu’à ce que l’application reçoive un message [WM_QUIT](/windows/win32/winmsg/wm-quit) . Si la file d’attente de messages du thread ne contient actuellement aucun message, les `Run` appels `OnIdle` pour effectuer le traitement au moment de l’inactivité. Les messages entrants sont envoyés à la fonction membre [PreTranslateMessage](#pretranslatemessage) pour un traitement spécial, puis à la fonction Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) pour la traduction du clavier standard. Enfin, la fonction Windows [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) est appelée.

`Run` est rarement substitué, mais vous pouvez le remplacer pour implémenter un comportement spécial.

Cette fonction membre est utilisée uniquement dans les threads d’interface utilisateur.

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a> CWinThread :: SetThreadPriority

Cette fonction définit le niveau de priorité du thread actuel dans sa classe de priorité.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Paramètres

*nPriority*<br/>
Spécifie le nouveau niveau de priorité de thread dans sa classe de priorité. Ce paramètre doit avoir l’une des valeurs suivantes, de la plus haute à la plus faible :

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Pour plus d’informations sur ces priorités, consultez [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Elle peut uniquement être appelée une fois que [CreateThread](#createthread) a été retourné avec succès.

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a> CWinThread :: SuspendThread

Incrémente le nombre de suspensions du thread actuel.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de suspensions précédentes du thread en cas de réussite ; `0xFFFFFFFF` sinon,.

### <a name="remarks"></a>Notes

Si un thread a un nombre d’interruptions supérieur à zéro, ce thread ne s’exécute pas. Le thread peut être repris en appelant la fonction membre [ResumeThread](#resumethread) .

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWinApp (classe)](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
