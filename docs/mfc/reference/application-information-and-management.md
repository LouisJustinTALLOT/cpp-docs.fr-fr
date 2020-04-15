---
title: Informations sur l'application et gestion
description: Référence aux fonctions d’information et de gestion des applications microsoft Foundation Class (MFC).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: fc0b4b09f6c48da68bebe4a2825f49bcf6ab7e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372501"
---
# <a name="application-information-and-management"></a>Informations sur l'application et gestion

Lorsque vous écrivez une application, vous créez un seul objet dérivé de [CWinApp.](../../mfc/reference/cwinapp-class.md) Parfois, vous pouvez obtenir des informations sur `CWinApp`cet objet de l’extérieur de l’objet dérivé. Ou vous pouvez avoir besoin d’accéder à d’autres objets « gestionnaires » mondiaux.

La Microsoft Foundation Class Library fournit les fonctions globales suivantes pour vous aider à accomplir ces tâches :

## <a name="application-information-and-management-functions"></a>Fonctions d’information et de gestion des applications

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Crée un nouveau thread.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Pointeur vers le gestionnaire de [menu contexte](ccontextmenumanager-class.md)global .|
|[AfxEndThread](#afxendthread)|Termine le fil actuel.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Parillons de la chaîne des ressources et localise une ressource spécifique par pièce d’identité et type de ressources. |
|[AfxFreeLibrary](#afxfreelibrary)|Décrément le nombre de références du module chargé de bibliothèque à liaison dynamique (DLL). Lorsque le nombre de références atteint zéro, le module n’est pas cartographié.|
|[AfxGetApp](#afxgetapp)|Renvoie un pointeur sur `CWinApp` l’objet unique de l’application.|
|[AfxGetAppName](#afxgetappname)|Renvoie une chaîne qui contient le nom de l’application.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Renvoie un HINSTANCE représentant cette instance de la demande.|
|[AfxGetMainWnd](#afxgetmainwnd)|Renvoie un pointeur à la fenêtre « principale » actuelle d’une application non-OLE, ou à la fenêtre de cadre place d’une application serveur.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Utilisez cette fonction pour déterminer si l’application redirige l’accès au registre au **nœud HKEY_CURRENT_USER** (**HKCU).**|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Renvoie un HINSTANCE à la source des ressources par défaut de l’application. Utiliser directement pour accéder directement aux ressources de l’application.|
|[AfxGetThread](#afxgetthread)|Récupère un pointeur sur l’objet [CWinThread](../../mfc/reference/cwinthread-class.md) actuel.|
|[AfxInitRichEdit](#afxinitrichedit)|Initialise la version 1.0 riche contrôle de modification pour l’application.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Initialise la version 2.0 et plus tard riche contrôle de modification pour l’application.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Détermine si la fenêtre donnée est un objet frame étendu.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Détermine si la fenêtre donnée est un objet de barre d’outils.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Pointeur vers le gestionnaire de [clavier](ckeyboardmanager-class.md)global .|
|[AfxLoadLibrary](#afxloadlibrary)|Cartographiez un module DLL et renvoie une poignée qui peut être utilisée pour obtenir l’adresse d’une fonction DLL.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Cartographiez un module DLL à l’aide des options spécifiées, et renvoie une poignée qui peut être utilisée pour obtenir l’adresse d’une fonction DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Pointeur vers le gestionnaire de [menu de déchirure](cmenutearoffmanager-class.md)globale .|
|[AfxMouseManager](#afxmousemanager)|Pointeur au gestionnaire mondial [de souris](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Enregistre un cours de fenêtre dans un DLL qui utilise MFC.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Enregistre une classe de fenêtre Windows pour compléter ceux enregistrés automatiquement par MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Définit si l’application redirige l’accès au registre vers le **nœud HKEY_CURRENT_USER** (**HKCU).**|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Définit la poignée HINSTANCE lorsque les ressources par défaut de l’application sont chargées.|
|[AfxShellManager](#afxshellmanager)|Pointeur au gestionnaire global [de coquille](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Appelé dans `CWinApp::InitInstance` un remplacement pour initialiser Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Pointeur vers le gestionnaire mondial [d’outils utilisateur](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Appelé par la fonction `WinMain` MFC-fourni, dans le cadre de l’initialisation [CWinApp](../../mfc/reference/cwinapp-class.md) d’une application basée sur l’interface graphique, pour initialiser MFC. Doit être appelé directement pour les applications de console qui utilisent MFC.|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a>AfxBeginThread

Appelez cette fonction pour créer un nouveau thread.

```cpp
CWinThread* AfxBeginThread(
    AFX_THREADPROC pfnThreadProc,
    LPVOID pParam,
    int nPriority = THREAD_PRIORITY_NORMAL,
    UINT nStackSize = 0,
    DWORD dwCreateFlags = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);

CWinThread* AfxBeginThread(
    CRuntimeClass* pThreadClass,
    int nPriority = THREAD_PRIORITY_NORMAL,
    UINT nStackSize = 0,
    DWORD dwCreateFlags = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Paramètres

*pfnThreadProc*\
Indique la fonction de contrôle du thread du travailleur. Le pointeur ne peut pas être NULL. Cette fonction doit être déclarée comme suit :

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass (en)*\
Le RUNTIME_CLASS d’un objet dérivé de [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam pParam*\
Paramètre pour passer à la fonction de contrôle.

*nPriorité*\
La priorité à définir pour le fil. Pour une liste complète et une description des priorités disponibles, voir [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

*nStackSize (en)*\
Specifie la taille des octets de la pile pour le nouveau fil. Si 0, la taille de la pile par défaut à la même pile de taille que le fil de création.

*dwCreateFlags dwCreateFlags dwCreateFlags dw*\
Spécifie un drapeau supplémentaire qui contrôle la création du fil. Ce drapeau peut contenir l’une des deux valeurs :

- CREATE_SUSPENDED Démarrer le fil avec un compte de suspension d’un. Utilisez CREATE_SUSPENDED si vous souhaitez parasminer les `CWinThread` données des membres de l’objet, telles que [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) ou tout membre de votre classe dérivée, avant que le thread ne commence à fonctionner. Une fois votre initialisation terminée, utilisez [CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) pour démarrer le thread en cours d’exécution. Le thread ne s’exécute pas tant qu’on ne l’appellera `CWinThread::ResumeThread` pas.

- **0** Démarrer le fil immédiatement après la création.

*lpSecurityAttrs*\
Indique une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie les attributs de sécurité pour le thread. Si NULL, les mêmes attributs de sécurité que le fil de création sont utilisés. Pour plus d’informations sur cette structure, voir le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet de fil nouvellement créé, ou NULL si une défaillance se produit.

### <a name="remarks"></a>Notes

La première `AfxBeginThread` forme de crée un fil de travail. La deuxième forme crée un thread qui peut servir de thread utilisateur-interface ou de thread de travailleur.

`AfxBeginThread`crée un `CWinThread` nouvel objet, appelle sa fonction [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) pour commencer à exécuter le thread, et renvoie un pointeur sur le thread. Des vérifications sont effectuées tout au long de la procédure pour s’assurer que tous les objets sont correctement répartis en cas d’échec d’une partie de la création. Pour mettre fin au thread, appelez [AfxEndThread](#afxendthread) à partir du thread, ou revenez de la fonction de contrôle du fil du travailleur.

La multilecture doit être activée par l’application ; sinon, cette fonction échouera. Pour plus d’informations sur l’activation de la multithreading, voir [/MD, /MT, /LD (Utilisez la bibliothèque de temps d’exécution)](../../build/reference/md-mt-ld-use-run-time-library.md).

Pour plus `AfxBeginThread`d’informations sur , voir les articles [Multithreading: Creating Worker Threads](../../parallel/multithreading-creating-worker-threads.md) and [Multithreading: Creating User-Interface Threads](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Exemple

Voir l’exemple pour [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a>AfxContextMenuManager

Pointeur vers le gestionnaire de [menu contexte](ccontextmenumanager-class.md)global .

### <a name="syntax"></a>Syntaxe

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxcontextmenumanager.h

## <a name="afxendthread"></a><a name="afxendthread"></a>AfxEndThread

Appelez cette fonction pour mettre fin au thread d’exécution actuel.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Paramètres

*nExitCode (en anglais)*\
Spécifie le code de sortie du fil.

*bDelete*\
Supprime l’objet de fil de la mémoire.

### <a name="remarks"></a>Notes

Doit être appelé de l’intérieur du fil pour être terminé.

Pour plus `AfxEndThread`d’informations sur , voir l’article [Multithreading: Terminating Threads](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a>AfxFindResourceHandle AfxFindResourceHandle

Utilisez `AfxFindResourceHandle` pour marcher dans la chaîne des ressources et localiser une ressource spécifique par pièce d’identité et type de ressources.

### <a name="syntax"></a>Syntaxe

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*\
Un pointeur à une chaîne contenant l’ID de ressource.
*lpszType (lpszType)*\
Un pointeur sur le type de ressource. Pour une liste des types de ressources, voir [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Une poignée au module qui contient la ressource.

### <a name="remarks"></a>Notes

`AfxFindResourceHandle`trouve la ressource spécifique, et renvoie une poignée au module qui contient la ressource. La ressource pourrait être dans n’importe quelle extension MFC DLL qui est chargé. `AfxFindResourceHandle`vous indique lequel a la ressource.

Les modules sont recherchés dans cet ordre :

1. Le module principal, s’il s’agit d’une extension MFC DLL.

1. Modules non système.

1. Modules spécifiques à la langue.

1. Le module principal, si c’est un système DLL.

1. Modules système.

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a>AfxFreeLibrary

Les `AfxFreeLibrary` `AfxLoadLibrary` deux et de maintenir un compte de référence pour chaque module de bibliothèque chargé.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Paramètres

*hInstLib*\
Une poignée du module de bibliothèque chargé. [AfxLoadLibrary](#afxloadlibrary) renvoie cette poignée.

### <a name="return-value"></a>Valeur de retour

VRAI si la fonction réussit; autrement, FALSE.

### <a name="remarks"></a>Notes

`AfxFreeLibrary`décrète le nombre de références du module chargé de bibliothèque à liaison dynamique (DLL). Lorsque le nombre de références atteint zéro, le module n’est pas cartographié à partir de l’espace d’adresse du processus d’appel et la poignée n’est plus valide. Ce nombre de références est `AfxLoadLibrary` incrémenté chaque fois qu’on s’appelle.

Avant de déballer un module de bibliothèque, le système permet au DLL de se détacher des processus qui l’utilisent. Cela donne au DLL l’occasion de nettoyer les ressources allouées pour le processus actuel. Une fois la fonction d’entrée, le module de bibliothèque est supprimé de l’espace d’adresse du processus actuel.

Utilisez `AfxLoadLibrary` pour cartographier un module DLL.

Assurez-vous `AfxFreeLibrary` d’utiliser `AfxLoadLibrary` et (au lieu `FreeLibrary` `LoadLibrary`des fonctions Win32 et ) si votre application utilise plusieurs threads. L’utilisation `AfxLoadLibrary` et `AfxFreeLibrary` la sécurité que le code de démarrage et d’arrêt qui s’exécute lorsque l’extension MFC DLL est chargé et déchargé ne corrompt pas l’état mondial MFC.

### <a name="example"></a>Exemple

Voir l’exemple pour [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdll_.h

## <a name="afxgetapp"></a><a name="afxgetapp"></a>AfxGetApp (en)

Le pointeur retourné par cette fonction peut être utilisé pour accéder aux informations d’application telles que le code principal de messagerie-expédition ou la fenêtre la plus haute.

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CWinApp` à l’objet unique pour l’application.

### <a name="remarks"></a>Notes

Si cette méthode renvoie NULL, elle peut indiquer que la fenêtre principale d’application n’a pas encore été entièrement parasitée. Il pourrait également indiquer un problème.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxgetappname"></a><a name="afxgetappname"></a>AfxGetAppName

La chaîne retournée peut être utilisée pour les messages diagnostiques, ou comme racine pour les noms de cordes temporaires.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Valeur de retour

Une chaîne non terminée contenant le nom de l’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a>AfxGetInstanceHandle

Cette fonction vous permet de récupérer la poignée d’instance de l’application actuelle.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Valeur de retour

Un HINSTANCE à l’instance actuelle de la demande. S’il est appelé à partir d’un DLL lié à la version USRDLL de MFC, un HINSTANCE à la DLL est retourné.

### <a name="remarks"></a>Notes

`AfxGetInstanceHandle`renvoie toujours le HINSTANCE de votre fichier exécutable (. EXE) à moins qu’il ne soit appelé de l’intérieur d’un DLL lié à la version USRDLL de MFC. Dans ce cas, il renvoie un HINSTANCE à la DLL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a>AfxGetMainWnd

Si votre application est un serveur OLE, appelez cette fonction pour récupérer un pointeur à la fenêtre principale active de l’application. Utilisez ce résultat au lieu de faire directement référence au [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) membre de l’objet d’application.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Valeur de retour

Renvoie un pointeur à l’objet de fenêtre de cadre qui contient le document actif en place, si le serveur a un objet qui est actif en place à l’intérieur d’un conteneur actif.

S’il n’y a pas d’objet actif dans un conteneur ou si votre application n’est pas un serveur OLE, cette fonction renvoie le *m_pMainWnd* de votre objet d’application.

Si `AfxGetMainWnd` elle est appelée à partir du fil principal de l’application, elle renvoie la fenêtre principale de l’application selon les règles ci-dessus. Si la fonction est appelée à partir d’un thread secondaire dans l’application, la fonction renvoie la fenêtre principale associée au thread qui a fait l’appel.

### <a name="remarks"></a>Notes

Si votre application n’est pas un serveur OLE, l’appel de cette fonction équivaut à se référer directement au *m_pMainWnd* membre de votre objet d’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a>AfxGetPerUserRegistration

Utilisez cette fonction pour déterminer si l’application redirige l’accès au registre au **nœud HKEY_CURRENT_USER** (**HKCU).**

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Valeur de retour

TRUE indique que les informations du registre sont dirigées vers le nœud HKCU. FALSE indique que la demande écrit des informations de registre au nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Notes

Si vous activez la réorientation du registre, le cadre redirige l’accès de **HKCR** à **HKEY_CURRENT_USER -Software-Classes**. Seuls les cadres MFC et ATL sont affectés par la redirection.

Pour modifier si l’application redirige l’accès au registre, utilisez [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Spécifications

  **En-tête** afxstat_.h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a>AfxGetResourceHandle AfxGetResourceHandle

Utilisez la poignée HINSTANCE retournée par cette fonction pour accéder directement aux ressources `FindResource`de l’application, par exemple, lors d’appels vers la fonction Windows .

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Valeur de retour

Une poignée HINSTANCE où les ressources par défaut de l’application sont chargées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxgetthread"></a><a name="afxgetthread"></a>AfxGetThread

Appelez cette fonction pour obtenir un pointeur à l’objet [CWinThread](../../mfc/reference/cwinthread-class.md) représentant le thread actuellement exécutant.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le fil d’exécution actuel; autrement NULL.

### <a name="remarks"></a>Notes

Doit être appelé de l’intérieur du fil.

> [!NOTE]
> Si vous transférez un projet `AfxGetThread` MFC à partir des versions Visual CMD 4.2, 5.0 ou 6.0, `AfxGetThread` appelle [AfxGetApp](#afxgetapp) si aucun thread n’est trouvé. Dans les versions plus récentes `AfxGetThread` du compilateur, retourne NULL si aucun thread n’a été trouvé. Si vous voulez le fil `AfxGetApp`d’application, vous devez appeler .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a>AfxInitRichEdit

Appelez cette fonction pour initialiser le contrôle d’édition riche (version 1.0) pour l’application.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Notes

Cette fonction est fournie pour la compatibilité vers l’arrière. Les nouvelles applications doivent utiliser [AfxInitRichEdit2](#afxinitrichedit2).

`AfxInitRichEdit`charges RICHED32. DLL pour initialiser la version 1.0 du contrôle d’édition riche. Pour utiliser les versions 2.0 et 3.0 du contrôle d’édition riche, RICHED20. DLL doit être chargé. Il est chargé en faisant un appel à [AfxInitRichEdit2](#afxinitrichedit2).

Pour mettre à jour les contrôles d’édition riches dans les applications Visual CMD existantes à la version 2.0, ouvrez le . Fichier RC comme texte, changer le nom de classe de chaque riche contrôle d’édition de "RICHEDIT" à "RichEdit20a". Ensuite, remplacez `AfxInitRichEdit` `AfxInitRichEdit2`l’appel par .

Cette fonction est également parasminée par la bibliothèque de contrôle commune, si la bibliothèque n’a pas encore été parascisée pour le processus. Si vous utilisez le contrôle d’édition riche directement à partir de votre application MFC, appelez cette fonction pour vous assurer que MFC a correctement paralysé le temps d’exécution de contrôle de modification riche. Si vous `Create` appelez la méthode de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), ou [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), vous n’avez généralement pas besoin d’appeler cette fonction, mais dans certains cas, il pourrait être nécessaire.

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a>AfxInitRichEdit2

Appelez cette fonction pour initialiser le contrôle d’édition riche (version 2.0 et plus tard) pour l’application.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour charger le RICHED20. DLL et initialiser la version 2.0 du contrôle d’édition riche. Si vous `Create` appelez la méthode de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), ou [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), vous n’avez généralement pas besoin d’appeler cette fonction, mais dans certains cas, il pourrait être nécessaire.

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass

Détermine si la fenêtre donnée est un objet frame étendu.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Paramètres

*Pwnd*\
[dans] Un pointeur à un `CWnd`objet qui est dérivé de .

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre fournie est un objet à cadre étendu; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode renvoie VRAI si *pWnd* dérive de l’une des classes suivantes:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Cette méthode est utile quand vous devez valider le fait qu’un paramètre de fonction ou de méthode est une fenêtre frame étendue.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a>AfxIsMFCToolBar

Détermine si la fenêtre donnée est un objet de barre d’outils.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*\
[dans] Un pointeur à un `CWnd`objet qui est dérivé de .

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre fournie est un objet de barre d’outils; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode `TRUE` revient si *pWnd* dérive de `CMFCToolBar`. Cette méthode est utile lorsque vous devez valider `CMFCToolBar` qu’un paramètre de fonction ou de méthode est un objet.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a>AfxKeyboardManager

Pointeur vers le gestionnaire de [clavier](ckeyboardmanager-class.md)global .

### <a name="syntax"></a>Syntaxe

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxkeyboardmanager.h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a>AfxLoadLibrary

Utilisez `AfxLoadLibrary` pour cartographier un module DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Paramètres

*lpszModuleName*\
Points à une chaîne non terminée qui contient le nom du module (soit un . DLL ou . Fichier EXE). Le nom spécifié est le nom de fichier du module.

Si la chaîne spécifie un chemin mais que le fichier n’existe pas dans l’annuaire spécifié, la fonction échoue.

Si un chemin n’est pas spécifié et que l’extension du nom de fichier est omise, l’extension par défaut . DLL est annexé. Cependant, la chaîne de nom de fichier peut inclure un caractère de point de fuite (.) pour indiquer que le nom du module n’a pas d’extension. Lorsqu’aucun chemin n’est spécifié, la fonction utilise [l’ordre de recherche pour les applications de bureau](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est une poignée au module. En cas d’échec, la valeur de retour est NULL.

### <a name="remarks"></a>Notes

Il renvoie une poignée qui peut être utilisée dans [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pour obtenir l’adresse d’une fonction DLL. `AfxLoadLibrary`peut également être utilisé pour cartographier d’autres modules exécutables.

Chaque processus maintient un compte de référence pour chaque module de bibliothèque chargé. Ce nombre de références est `AfxLoadLibrary` incrémenté chaque fois qu’on appelle et est décrmenté chaque fois `AfxFreeLibrary` qu’on appelle. Lorsque le nombre de références atteint zéro, le module n’est pas cartographié à partir de l’espace d’adresse du processus d’appel et la poignée n’est plus valide.

Assurez-vous `AfxLoadLibrary` d’utiliser `AfxFreeLibrary` et (au lieu `LoadLibrary` `FreeLibrary`des fonctions Win32 et ) si votre application utilise plusieurs threads, et si elle charge dynamiquement une extension MFC DLL. L’utilisation `AfxLoadLibrary` et `AfxFreeLibrary` l’assurance que le code de démarrage et d’arrêt qui exécute lorsque l’extension MFC DLL est chargée et déchargée ne corrompt pas l’état mondial MFC.

L’utilisation `AfxLoadLibrary` d’une application vous oblige à un lien dynamique vers la version DLL de MFC. Le fichier `AfxLoadLibrary`d’en-tête pour , Afxdll_.h, n’est inclus que si MFC est lié à l’application en tant que DLL. Cette exigence est de conception, parce que vous devez lier à la version DLL de MFC pour utiliser ou créer des DLL d’extension MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdll_.h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a>AfxLoadLibraryEx

Utilisez `AfxLoadLibraryEx` pour cartographier un module DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*lpFileName*\
Points à une chaîne non terminée qui contient le nom du module (soit un . DLL ou . Fichier EXE). Le nom spécifié est le nom de fichier du module.

Si la chaîne spécifie un chemin mais que le fichier n’existe pas dans l’annuaire spécifié, la fonction échoue.

Si un chemin n’est pas spécifié et que l’extension du nom de fichier est omise, l’extension par défaut . DLL est annexé. Cependant, la chaîne de nom de fichier peut inclure un caractère de point de fuite (.) pour indiquer que le nom du module n’a pas d’extension. Lorsqu’aucun chemin n’est spécifié, la fonction utilise [l’ordre de recherche pour les applications de bureau](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

*hFile (en)*\
Ce paramètre est réservé à un usage futur. Ce doit être NULL.

*dwFlags dwFlags*\
Les mesures à prendre lors du chargement du module. Si aucun signal n’est spécifié, le `AfxLoadLibrary` comportement de cette fonction est identique à la fonction. Les valeurs possibles de ce paramètre sont décrites dans la documentation [LoadLibraryEx.](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est une poignée au module. En cas d’échec, la valeur de retour est NULL.

### <a name="remarks"></a>Notes

`AfxLoadLibraryEx`retourne une poignée qui peut être utilisée dans [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pour obtenir l’adresse d’une fonction DLL. `AfxLoadLibraryEx`peut également être utilisé pour cartographier d’autres modules exécutables.

Chaque processus maintient un compte de référence pour chaque module de bibliothèque chargé. Ce nombre de références est `AfxLoadLibraryEx` incrémenté chaque fois qu’on appelle et est décrmenté chaque fois `AfxFreeLibrary` qu’on appelle. Lorsque le nombre de références atteint zéro, le module n’est pas cartographié à partir de l’espace d’adresse du processus d’appel et la poignée n’est plus valide.

Assurez-vous `AfxLoadLibraryEx` d’utiliser `AfxFreeLibrary` et (au lieu `LoadLibraryEx` `FreeLibrary`des fonctions Win32 et ) si votre application utilise plusieurs threads et si elle charge dynamiquement une extension MFC DLL. L’utilisation `AfxLoadLibraryEx` et `AfxFreeLibrary` la sécurité que le code de démarrage et d’arrêt qui s’exécute lorsque l’extension MFC DLL est chargé et déchargé ne corrompt pas l’état mondial MFC.

L’utilisation `AfxLoadLibraryEx` d’une application vous oblige à un lien dynamique vers la version DLL de MFC. Le fichier `AfxLoadLibraryEx`d’en-tête pour , Afxdll_.h, n’est inclus que si MFC est lié à l’application en tant que DLL. Cette exigence est de conception, parce que vous devez lier à la version DLL de MFC pour utiliser ou créer des DLL d’extension MFC.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdll_.h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

Pointeur vers le gestionnaire de [menu de déchirure](cmenutearoffmanager-class.md)globale .

### <a name="syntax"></a>Syntaxe

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxmenutearoffmanager.h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a>AfxMouseManager

Pointeur au gestionnaire mondial [de souris](cmousemanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxmousemanager.h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a>AfxRegisterClass (en)

Utilisez cette fonction pour enregistrer les classes de fenêtre dans un DLL qui utilise MFC.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Paramètres

*lpWndClass*\
Pointeur vers une structure [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) contenant des informations sur la classe de fenêtre à enregistrer. Pour plus d’informations sur cette structure, voir le SDK Windows.

### <a name="return-value"></a>Valeur de retour

VRAI si la classe est enregistrée avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Si vous utilisez cette fonction, la classe est automatiquement non enregistrée lorsque le DLL est déchargé.

Dans les versions non-DLL, l’identifiant `AfxRegisterClass` est défini `RegisterClass`comme une macro qui cartes à la fonction Windows , puisque les classes enregistrées dans une application sont automatiquement non enregistrées. Si vous `AfxRegisterClass` utilisez `RegisterClass`au lieu de , votre code peut être utilisé sans modification à la fois dans une application et dans un DLL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a>AfxRegisterWndClass

Permet d'enregistrer vos propres classes de fenêtre.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Paramètres

*nClassStyle (en)*\
Spécifie le style de la classe Windows ou la combinaison de styles, créé en utilisant l’opérateur bitwise-OR (**&#124;), **pour la classe de fenêtre. Pour une liste de styles de classe, voir la structure [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) dans le SDK Windows. Si NULL, les défauts sont définis comme suit :

- Définit le style de la souris sur CS_DBLCLKS, qui envoie des messages de double-clic à la procédure d'affichage lorsque l'utilisateur double-clique sur la souris.

- Définit le style du curseur flèche sur la valeur IDC_ARROW standard Windows.

- Définit la brosse de fond à NULL, de sorte que la fenêtre n’effacera pas son arrière-plan.

- Définit l'icône du logo Windows standard en forme de drapeau flottant.

*hCursor*\
Spécifie un handle pour la ressource curseur à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez le par défaut de **0**, vous obtiendrez le curseur standard IDC_ARROW.

*hbrBackground (en)*\
Spécifie un handle de la ressource pinceau à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez le défaut de **0**, vous aurez une brosse d’arrière-plan NULL, et par défaut, votre fenêtre n’effacera pas son arrière-plan tout en traitant [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

*hIcon (en)*\
Spécifie un handle de la ressource icône à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez la valeur par défaut de **0**, vous obtiendrez l’icône standard du logo Windows.

### <a name="return-value"></a>Valeur de retour

Chaîne de caractères se terminant par null et contenant le nom de la classe. Vous pouvez transmettre ce nom `Create` de `CWnd` classe à la fonction membre dans ou dans d’autres classes dérivées du **CWnd**pour créer une fenêtre. Le nom est généré par la bibliothèque MFC.

> [!NOTE]
> La valeur de retour est un pointeur vers une mémoire tampon statique. Pour enregistrer cette chaîne, attribuez-lui une variable `CString`.

### <a name="remarks"></a>Notes

La bibliothèque MFC stocke automatiquement plusieurs classes de fenêtre standard pour vous. Appelez cette fonction si vous souhaitez stocker vos propres classes de fenêtre.

Le nom enregistré pour une classe par `AfxRegisterWndClass` dépend uniquement des paramètres. Si vous appelez `AfxRegisterWndClass` plusieurs fois avec des paramètres identiques, seule une classe lors du premier appel est enregistrée. Les appels `AfxRegisterWndClass` ultérieurs avec des paramètres identiques renvoient le nom de classe déjà enregistré.

Si vous appelez `AfxRegisterWndClass` pour plusieurs classes dérivées de CWnd avec des paramètres identiques, au lieu d'obtenir une classe de fenêtre distincte pour chaque classe, chacune partagera la même classe de fenêtre. Ce partage peut causer des problèmes si le style de classe CS_CLASSDC est utilisé. Au lieu de plusieurs classes de fenêtre CS_CLASSDC, vous vous retrouvez avec une seule CS_CLASSDC classe de fenêtre. Toutes les fenêtres CMD qui utilisent cette classe partagent le même DC. Pour éviter ce problème, appelez [AfxRegisterClass](#afxregisterclass) pour enregistrer la classe.

Consultez la note technique [TN001: Enregistrement de classe](../../mfc/tn001-window-class-registration.md) de `AfxRegisterWndClass` fenêtre pour plus d’informations sur l’inscription de la classe de fenêtre et la fonction.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a>AfxSetPerUserRegistration

Définit si l’application redirige l’accès au registre vers le **nœud HKEY_CURRENT_USER** (**HKCU).**

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*\
[dans] TRUE indique que les informations du registre sont dirigées vers le nœud HKCU. FALSE indique que la demande écrit des informations de registre au nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Notes

Avant Windows Vista, les applications qui accédaient au registre utilisaient couramment le **nœud HKEY_CLASSES_ROOT.** Cependant, avec Windows Vista ou des systèmes d’exploitation ultérieurs, vous devez exécuter une application en mode élevé pour écrire à HKCR.

Cette méthode permet à votre application de lire et d’écrire au registre sans courir en mode élevé. Il fonctionne en redirigeant l’accès au registre de HKCR à HKCU. Pour plus d’informations, voir [Pages de propriété Linker](../../build/reference/linker-property-pages.md).

Si vous activez la réorientation du registre, le cadre redirige l’accès de HKCR à **HKEY_CURRENT_USER -Software-Classes**. Seuls les cadres MFC et ATL sont affectés par la redirection.

La mise en œuvre par défaut accède au registre en vertu de HKCR.

### <a name="requirements"></a>Spécifications

  **En-tête** afxstat_.h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a>AfxSetResourceHandle AfxSetResourceHandle

Utilisez cette fonction pour définir la poignée HINSTANCE qui détermine où les ressources par défaut de l’application sont chargées.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Paramètres

*hInstResource*\
L’instance ou le module poignée à un . Fichier EXE ou DLL à partir duquel les ressources de l’application sont chargées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a>AfxShellManager

Pointeur au gestionnaire global [de coquille](cshellmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxshellmanager.h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a>AfxSocketInit

Appelez cette fonction `CWinApp::InitInstance` dans votre remplacement pour initialiser windows Sockets.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Paramètres

*lpwsaData lpwsaData*\
Un pointeur vers une structure [WSADATA.](/windows/win32/api/winsock2/ns-winsock2-wsadata) Si *lpwsaData* n’est pas égal à `WSADATA` NULL, alors l’adresse de la structure est remplie par l’appel à `WSAStartup`. Cette fonction garantit `WSACleanup` également que cela est appelé pour vous avant la fin de l’application.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Lorsque vous utilisez des prises MFC dans des threads secondaires dans `AfxSocketInit` une application MFC statiquement liée, vous devez appeler dans chaque thread qui utilise des prises pour initialiser les bibliothèques de prises. Par défaut, `AfxSocketInit` est appelé uniquement dans le fil principal.

### <a name="requirements"></a>Spécifications

  **En-tête** afxsock.h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a>AfxUserToolsManager

Pointeur vers le gestionnaire mondial [d’outils utilisateur](cusertoolsmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxusertoolsmanager.h

## <a name="afxwininit"></a><a name="afxwininit"></a>AfxWinInit AfxWinInit

Cette fonction est appelée par `WinMain` la fonction fournie par MFC, dans le cadre de l’initialisation [CWinApp](../../mfc/reference/cwinapp-class.md) d’une application basée sur l’INTERFACE graphique, pour initialiser MFC.

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Paramètres

*hInstance*\
La poignée du module actuellement en cours d’exécution.

*hPrevInstance*\
Une poignée à une instance précédente de la demande. Pour une application basée sur Win32, ce paramètre est toujours **NULL**.

*lpCmdLine (en)*\
Indique une chaîne non terminée précisant la ligne de commande de l’application.

*nCmdShow (en)*\
Précise comment la fenêtre principale d’une application d’interface graphique serait affichée.

### <a name="remarks"></a>Notes

Pour une application de console, qui n’utilise pas la fonction fournie par `WinMain` MFC, vous devez appeler `AfxWinInit` directement pour initialiser MFC.

Si vous `AfxWinInit` vous appelez vous-même, `CWinApp` vous devez déclarer un exemple de classe. Pour une application de console, vous pouvez `CWinApp` choisir de ne `CWinApp` pas tirer votre propre classe de et plutôt utiliser une instance de directement. Cette technique est appropriée si vous décidez de laisser toutes les fonctionnalités pour votre application dans votre implémentation de **main**.

> [!NOTE]
> Lorsqu’il crée un contexte d’activation pour un assemblage, MFC utilise une ressource manifeste fournie par le module utilisateur. Le contexte d’activation est créé en `AfxWinInit`. Pour plus d’informations, voir [Support for Activation Contexts in the MFC Module State](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="see-also"></a>Voir aussi

[Macros et globals](mfc-macros-and-globals.md)\
[Classe CWinApp](cwinapp-class.md)\
[Classe CContextMenuManager](ccontextmenumanager-class.md)\
[Classe CWnd](cwnd-class.md)\
[Classe CFrameWndEx](cframewndex-class.md)\
[Classe CMFCToolBar](cmfctoolbar-class.md)\
[Classe CKeyboardManager](ckeyboardmanager-class.md)\
[Classe CMenuTearOffManager](cmenutearoffmanager-class.md)\
[Classe CMouseManager](cmousemanager-class.md)\
[Classe CShellManager](cshellmanager-class.md)\
[Classe CUserToolsManager](cusertoolsmanager-class.md)
