---
title: Informations sur l'application et gestion
description: Référence aux fonctions de gestion et informations de l’application de la bibliothèque MFC (Microsoft Foundation Class).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: 3412ed3f02e93d3e8c947d4f730355c219493a77
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832305"
---
# <a name="application-information-and-management"></a>Informations sur l'application et gestion

Lorsque vous écrivez une application, vous créez un seul objet dérivé de [CWinApp](../../mfc/reference/cwinapp-class.md). Dans certains cas, vous souhaiterez peut-être obtenir des informations sur cet objet en dehors de l' `CWinApp` objet dérivé de. Ou vous pouvez avoir besoin d’accéder à d’autres objets « Manager » globaux.

L’bibliothèque MFC (Microsoft Foundation Class) fournit les fonctions globales suivantes pour vous aider à accomplir ces tâches :

## <a name="application-information-and-management-functions"></a>Fonctions de gestion et informations sur l’application

| Nom | Description |
|-|-|
|[AfxBeginThread](#afxbeginthread)|Crée un nouveau thread.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Pointeur vers le [Gestionnaire de menu contextuel](ccontextmenumanager-class.md)global.|
|[AfxEndThread](#afxendthread)|Termine le thread actuel.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Parcourt la chaîne de ressources et recherche une ressource spécifique par l’ID de ressource et le type de ressource. |
|[AfxFreeLibrary](#afxfreelibrary)|Décrémente le décompte de références du module de bibliothèque de liens dynamiques (DLL) chargé. Lorsque le nombre de références atteint zéro, le module n’est pas mappé.|
|[AfxGetApp](#afxgetapp)|Retourne un pointeur vers l’objet unique de l’application `CWinApp` .|
|[AfxGetAppName](#afxgetappname)|Retourne une chaîne qui contient le nom de l’application.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Retourne un HINSTANCE représentant cette instance de l’application.|
|[AfxGetMainWnd](#afxgetmainwnd)|Retourne un pointeur désignant la fenêtre « principale » active d’une application non-OLE, ou la fenêtre frame sur place d’une application serveur.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Utilisez cette fonction pour déterminer si l’application redirige l’accès au registre vers le nœud **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Retourne un HINSTANCE à la source des ressources par défaut de l’application. Utilisez pour accéder directement aux ressources de l’application.|
|[AfxGetThread](#afxgetthread)|Récupère un pointeur vers l’objet [CWinThread](../../mfc/reference/cwinthread-class.md) actuel.|
|[AfxInitRichEdit](#afxinitrichedit)|Initialise le contrôle RichEdit version 1,0 pour l’application.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Initialise le contrôle Rich Edit version 2,0 et ultérieur pour l’application.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Détermine si la fenêtre donnée est un objet frame étendu.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Détermine si la fenêtre donnée est un objet Toolbar.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Pointeur vers le [Gestionnaire de clavier](ckeyboardmanager-class.md)global.|
|[AfxLoadLibrary](#afxloadlibrary)|Mappe un module DLL et retourne un handle qui peut être utilisé pour obtenir l’adresse d’une fonction DLL.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Mappe un module DLL à l’aide des options spécifiées et retourne un handle qui peut être utilisé pour obtenir l’adresse d’une fonction DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Pointeur désignant le [Gestionnaire de menus détachements](cmenutearoffmanager-class.md)globaux.|
|[AfxMouseManager](#afxmousemanager)|Pointeur vers le [Gestionnaire de souris](cmousemanager-class.md)global.|
|[AfxRegisterClass](#afxregisterclass)|Inscrit une classe de fenêtre dans une DLL qui utilise MFC.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Inscrit une classe de fenêtre Windows pour compléter celles inscrites automatiquement par MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Définit si l’application redirige l’accès au registre vers le nœud **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Définit le handle HINSTANCE dans lequel les ressources par défaut de l’application sont chargées.|
|[AfxShellManager](#afxshellmanager)|Pointeur vers le [Gestionnaire d’interpréteur](cshellmanager-class.md)de commandes global. |
|[AfxSocketInit](#afxsocketinit)|Appelé dans une `CWinApp::InitInstance` substitution pour initialiser Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Pointeur vers le [Gestionnaire des outils utilisateur](cusertoolsmanager-class.md)globaux.|
|[AfxWinInit](#afxwininit)|Appelée par la fonction fournie par MFC `WinMain` , dans le cadre de l’initialisation [CWinApp](../../mfc/reference/cwinapp-class.md) d’une application basée sur l’interface graphique utilisateur, pour initialiser MFC. Doit être appelé directement pour les applications console qui utilisent MFC.|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a> AfxBeginThread

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
Pointe vers la fonction de contrôle du thread de travail. Le pointeur ne peut pas être NULL. Cette fonction doit être déclarée comme suit :

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*\
RUNTIME_CLASS d’un objet dérivé de [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*\
Paramètre à passer à la fonction de contrôle.

*nPriority*\
Priorité à définir pour le thread. Pour obtenir une liste complète et une description des priorités disponibles, consultez [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

*nStackSize*\
Spécifie la taille en octets de la pile pour le nouveau thread. Si la valeur est 0, la taille de la pile est par défaut la même pile de taille que le thread de création.

*dwCreateFlags*\
Spécifie un indicateur supplémentaire qui contrôle la création du thread. Cet indicateur peut contenir l’une des deux valeurs suivantes :

- CREATE_SUSPENDED démarrer le thread avec un nombre de suspension d’un. Utilisez CREATE_SUSPENDED si vous souhaitez initialiser toutes les données de membre de l' `CWinThread` objet, telles que [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) ou les membres de votre classe dérivée, avant que le thread ne commence à s’exécuter. Une fois l’initialisation terminée, utilisez [CWinThread :: ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) pour démarrer le thread en cours d’exécution. Le thread ne s’exécute pas tant que `CWinThread::ResumeThread` n’est pas appelé.

- **0** démarre le thread immédiatement après la création.

*lpSecurityAttrs*\
Pointe vers une structure de [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie les attributs de sécurité du thread. Si la valeur est NULL, les mêmes attributs de sécurité que le thread de création sont utilisés. Pour plus d’informations sur cette structure, consultez la SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet de thread nouvellement créé, ou NULL si une erreur se produit.

### <a name="remarks"></a>Notes

La première forme de `AfxBeginThread` crée un thread de travail. Le deuxième formulaire crée un thread qui peut servir de thread d’interface utilisateur ou de thread de travail.

`AfxBeginThread` crée un `CWinThread` objet, appelle sa fonction [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) pour démarrer l’exécution du thread et retourne un pointeur vers le thread. Les vérifications sont effectuées tout au long de la procédure pour s’assurer que tous les objets sont désalloués correctement en cas d’échec d’une partie de la création. Pour terminer le thread, appelez [AfxEndThread](#afxendthread) à partir du thread, ou retournez à partir de la fonction de contrôle du thread de travail.

Le multithreading doit être activé par l’application ; dans le cas contraire, cette fonction échoue. Pour plus d’informations sur l’activation du multithreading, consultez [/MD,/MT,/LD (utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md).

Pour plus d’informations sur `AfxBeginThread` , consultez les articles sur le [Multithreading : création de threads de travail](../../parallel/multithreading-creating-worker-threads.md) et [Multithreading : création de threads d’interface utilisateur](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Exemple

Consultez l’exemple pour [CSocket :: Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a> AfxContextMenuManager

Pointeur vers le [Gestionnaire de menu contextuel](ccontextmenumanager-class.md)global.

### <a name="syntax"></a>Syntaxe

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxcontextmenumanager. h

## <a name="afxendthread"></a><a name="afxendthread"></a> AfxEndThread

Appelez cette fonction pour terminer le thread en cours d’exécution.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Paramètres

*nExitCode*\
Spécifie le code de sortie du thread.

*bSupprimer*\
Supprime l’objet thread de la mémoire.

### <a name="remarks"></a>Notes

Doit être appelé à partir du thread à arrêter.

Pour plus d’informations sur `AfxEndThread` , consultez l’article sur le [Multithreading : arrêt des threads](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a> AfxFindResourceHandle

Utilisez `AfxFindResourceHandle` pour parcourir la chaîne de ressources et rechercher une ressource spécifique par l’ID de ressource et le type de ressource.

### <a name="syntax"></a>Syntaxe

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Paramètres

*lpszName*\
Pointeur vers une chaîne contenant l’ID de ressource.
*lpszType*\
Pointeur vers le type de ressource. Pour obtenir la liste des types de ressources, consultez [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Handle du module qui contient la ressource.

### <a name="remarks"></a>Notes

`AfxFindResourceHandle` recherche la ressource spécifique et retourne un handle au module qui contient la ressource. La ressource peut être dans n’importe quelle DLL d’extension MFC chargée. `AfxFindResourceHandle` indique la ressource qui contient la ressource.

Les modules sont recherchés dans l’ordre suivant :

1. Module principal, s’il s’agit d’une DLL d’extension MFC.

1. Modules non-système.

1. Modules spécifiques à une langue.

1. Le module principal, s’il s’agit d’une DLL système.

1. Modules système.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a> AfxFreeLibrary

`AfxFreeLibrary`Et `AfxLoadLibrary` gèrent un décompte de références pour chaque module de bibliothèque chargé.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Paramètres

*hInstLib*\
Handle du module de bibliothèque chargé. [AfxLoadLibrary](#afxloadlibrary) retourne ce descripteur.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fonction est réussie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

`AfxFreeLibrary` décrémente le décompte de références du module de bibliothèque de liens dynamiques (DLL) chargé. Lorsque le décompte de références atteint zéro, le module n’est pas mappé à partir de l’espace d’adressage du processus appelant et le handle n’est plus valide. Ce nombre de références est incrémenté chaque fois que `AfxLoadLibrary` est appelé.

Avant de démapper un module de bibliothèque, le système permet à la DLL de se détacher des processus qui l’utilisent. Cela permet à la DLL de nettoyer les ressources allouées pour le processus actuel. Une fois la fonction de point d’entrée retournée, le module de bibliothèque est supprimé de l’espace d’adressage du processus en cours.

Utilisez `AfxLoadLibrary` pour mapper un module dll.

Veillez à utiliser `AfxFreeLibrary` et `AfxLoadLibrary` (au lieu des fonctions Win32 `FreeLibrary` et `LoadLibrary` ) si votre application utilise plusieurs threads. L’utilisation `AfxLoadLibrary` de et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la dll d’extension MFC est chargée et déchargée n’endommage pas l’état global des MFC.

### <a name="example"></a>Exemple

Consultez l’exemple pour [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdll_. h

## <a name="afxgetapp"></a><a name="afxgetapp"></a> AfxGetApp

Le pointeur retourné par cette fonction peut être utilisé pour accéder aux informations de l’application, telles que le code principal de distribution de messages ou la fenêtre de premier plan.

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet unique `CWinApp` pour l’application.

### <a name="remarks"></a>Notes

Si cette méthode retourne la valeur NULL, cela peut indiquer que la fenêtre principale de l’application n’a pas encore été complètement initialisée. Cela peut également indiquer un problème.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxgetappname"></a><a name="afxgetappname"></a> AfxGetAppName

La chaîne retournée peut être utilisée pour les messages de diagnostic ou comme racine pour les noms de chaîne temporaires.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Valeur renvoyée

Chaîne terminée par le caractère null qui contient le nom de l’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a> AfxGetInstanceHandle

Cette fonction vous permet de récupérer le handle d’instance de l’application actuelle.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Valeur renvoyée

HINSTANCE de l’instance actuelle de l’application. Si elle est appelée à partir d’une DLL liée à la version USRDLL de MFC, un HINSTANCE à la DLL est retourné.

### <a name="remarks"></a>Notes

`AfxGetInstanceHandle` retourne toujours le HINSTANCE de votre fichier exécutable (. EXE), sauf s’il est appelé à partir d’une DLL liée à la version USRDLL de MFC. Dans ce cas, elle retourne un HINSTANCE à la DLL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a> AfxGetMainWnd

Si votre application est un serveur OLE, appelez cette fonction pour récupérer un pointeur vers la fenêtre principale active de l’application. Utilisez ce résultat au lieu de faire directement référence au [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) membre de l’objet d’application.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers l’objet de fenêtre frame qui contient le document actif sur place, si le serveur a un objet qui est actif sur place à l’intérieur d’un conteneur actif.

Si aucun objet n’est actif sur place au sein d’un conteneur, ou si votre application n’est pas un serveur OLE, cette fonction retourne le *m_pMainWnd* de votre objet application.

Si `AfxGetMainWnd` est appelé à partir du thread principal de l’application, il retourne la fenêtre principale de l’application conformément aux règles ci-dessus. Si la fonction est appelée à partir d’un thread secondaire dans l’application, la fonction retourne la fenêtre principale associée au thread qui a effectué l’appel.

### <a name="remarks"></a>Notes

Si votre application n’est pas un serveur OLE, l’appel de cette fonction équivaut à référencer directement le membre *m_pMainWnd* de votre objet application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a> AfxGetPerUserRegistration

Utilisez cette fonction pour déterminer si l’application redirige l’accès au registre vers le nœud **HKEY_CURRENT_USER** (**HKCU**).

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE indique que les informations du Registre sont dirigées vers le nœud HKCU. FALSe indique que l’application écrit les informations de Registre dans le nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Notes

Si vous activez la redirection du Registre, le Framework redirige l’accès de **HKCR** vers **HKEY_CURRENT_USER \Software\Classes**. Seuls les frameworks MFC et ATL sont affectés par la redirection.

Pour changer si l’application redirige l’accès au registre, utilisez [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxstat_. h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a> AfxGetResourceHandle

Utilisez le handle HINSTANCE retourné par cette fonction pour accéder directement aux ressources de l’application, par exemple, dans les appels à la fonction Windows `FindResource` .

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Valeur renvoyée

Handle HINSTANCE dans lequel les ressources par défaut de l’application sont chargées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxgetthread"></a><a name="afxgetthread"></a> AfxGetThread

Appelez cette fonction pour obtenir un pointeur vers l’objet [CWinThread](../../mfc/reference/cwinthread-class.md) représentant le thread en cours d’exécution.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le thread en cours d’exécution ; Sinon, NULL.

### <a name="remarks"></a>Notes

Doit être appelé à partir du thread.

> [!NOTE]
> Si vous portez un projet MFC appelant `AfxGetThread` à partir de Visual C++ versions 4,2, 5,0 ou 6,0, `AfxGetThread` appelle [AfxGetApp](#afxgetapp) si aucun thread n’est trouvé. Dans les versions plus récentes du compilateur, `AfxGetThread` retourne la valeur null si aucun thread n’a été trouvé. Si vous souhaitez utiliser le thread d’application, vous devez appeler `AfxGetApp` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a> AfxInitRichEdit

Appelez cette fonction pour initialiser le contrôle Rich Edit (version 1,0) de l’application.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Notes

Cette fonction est fournie à des fins de compatibilité descendante. Les nouvelles applications doivent utiliser [AfxInitRichEdit2](#afxinitrichedit2).

`AfxInitRichEdit` charge RICHED32.DLL pour initialiser la version 1,0 du contrôle Rich Edit. Pour utiliser la version 2,0 et 3,0 du contrôle Rich Edit, RICHED20.DLL doit être chargé. Elle est chargée en effectuant un appel à [AfxInitRichEdit2](#afxinitrichedit2).

Pour mettre à jour les contrôles RichEdit des applications Visual C++ existantes vers la version 2,0, ouvrez le. Fichier RC en tant que texte, remplacez le nom de classe de chaque contrôle Rich Edit « RICHEDIT » par « RichEdit20a ». Remplacez ensuite l’appel à `AfxInitRichEdit` par `AfxInitRichEdit2` .

Cette fonction initialise également la bibliothèque de contrôles communs, si la bibliothèque n’a pas déjà été initialisée pour le processus. Si vous utilisez le contrôle Rich Edit directement à partir de votre application MFC, appelez cette fonction pour vous assurer que MFC a correctement initialisé le runtime de contrôle RichEdit. Si vous appelez la `Create` méthode de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)ou [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), vous n’avez généralement pas besoin d’appeler cette fonction, mais dans certains cas, cela peut s’avérer nécessaire.

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a> AfxInitRichEdit2

Appelez cette fonction pour initialiser le contrôle Rich Edit (version 2,0 et ultérieure) pour l’application.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour charger le RICHED20.DLL et initialiser la version 2,0 du contrôle Rich Edit. Si vous appelez la `Create` méthode de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)ou [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), vous n’avez généralement pas besoin d’appeler cette fonction, mais dans certains cas, cela peut s’avérer nécessaire.

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a> AfxIsExtendedFrameClass

Détermine si la fenêtre donnée est un objet frame étendu.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Paramètres

*pWnd*\
dans Pointeur vers un objet dérivé de `CWnd` .

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fenêtre fournie est un objet Frame étendu ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur TRUE si *pwnd* dérive de l’une des classes suivantes :

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Cette méthode est utile quand vous devez valider le fait qu’un paramètre de fonction ou de méthode est une fenêtre frame étendue.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxpriv.h

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a> AfxIsMFCToolBar

Détermine si la fenêtre donnée est un objet Toolbar.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*\
dans Pointeur vers un objet dérivé de `CWnd` .

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fenêtre fournie est un objet de barre d’outils ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode retourne `TRUE` si *pwnd* dérive de `CMFCToolBar` . Cette méthode est utile lorsque vous devez valider le fait qu’un paramètre de fonction ou de méthode est un `CMFCToolBar` objet.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxpriv.h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a> AfxKeyboardManager

Pointeur vers le [Gestionnaire de clavier](ckeyboardmanager-class.md)global.

### <a name="syntax"></a>Syntaxe

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxkeyboardmanager. h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a> AfxLoadLibrary

Utilisez `AfxLoadLibrary` pour mapper un module dll.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Paramètres

*lpszModuleName*\
Pointe vers une chaîne se terminant par un caractère null qui contient le nom du module (soit un. DLL ou. Fichier exécutable). Le nom spécifié est le nom du fichier du module.

Si la chaîne spécifie un chemin d’accès mais que le fichier n’existe pas dans le répertoire spécifié, la fonction échoue.

Si aucun chemin d’accès n’est spécifié et que l’extension de nom de fichier est omise, il s’agit de l’extension par défaut. La DLL est ajoutée. Toutefois, la chaîne de nom de fichier peut inclure un caractère de point de fin (.) pour indiquer que le nom du module n’a pas d’extension. Quand aucun chemin d’accès n’est spécifié, la fonction utilise l' [ordre de recherche pour les applications de bureau](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

### <a name="return-value"></a>Valeur renvoyée

Si la fonction est réussie, la valeur de retour est un handle du module. En cas d’échec, la valeur de retour est NULL.

### <a name="remarks"></a>Notes

Elle retourne un handle qui peut être utilisé dans [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pour obtenir l’adresse d’une fonction dll. `AfxLoadLibrary` peut également être utilisé pour mapper d’autres modules exécutables.

Chaque processus gère un décompte de références pour chaque module de bibliothèque chargé. Ce nombre de références est incrémenté chaque fois `AfxLoadLibrary` que est appelé et est décrémenté chaque fois que `AfxFreeLibrary` est appelé. Lorsque le décompte de références atteint zéro, le module n’est pas mappé à partir de l’espace d’adressage du processus appelant et le handle n’est plus valide.

Veillez à utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions Win32 `LoadLibrary` et `FreeLibrary` ) si votre application utilise plusieurs threads, et si elle charge dynamiquement une DLL d’extension MFC. L’utilisation `AfxLoadLibrary` de et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la dll d’extension MFC est chargée et déchargée n’endommage pas l’état global des MFC.

L’utilisation `AfxLoadLibrary` de dans une application vous oblige à établir une liaison dynamique à la version DLL de MFC. Le fichier d’en-tête pour `AfxLoadLibrary` , Afxdll_. h, est inclus uniquement si MFC est lié à l’application en tant que dll. Cette exigence est due à la conception, car vous devez établir une liaison à la version DLL de MFC pour utiliser ou créer des dll d’extension MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdll_. h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a> AfxLoadLibraryEx

Utilisez `AfxLoadLibraryEx` pour mapper un module dll.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*lpFileName*\
Pointe vers une chaîne se terminant par un caractère null qui contient le nom du module (soit un. DLL ou. Fichier exécutable). Le nom spécifié est le nom du fichier du module.

Si la chaîne spécifie un chemin d’accès mais que le fichier n’existe pas dans le répertoire spécifié, la fonction échoue.

Si aucun chemin d’accès n’est spécifié et que l’extension de nom de fichier est omise, il s’agit de l’extension par défaut. La DLL est ajoutée. Toutefois, la chaîne de nom de fichier peut inclure un caractère de point de fin (.) pour indiquer que le nom du module n’a pas d’extension. Quand aucun chemin d’accès n’est spécifié, la fonction utilise l' [ordre de recherche pour les applications de bureau](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

*hFile*\
Ce paramètre est réservé à un usage futur. La valeur doit être NULL.

*dwFlags*\
Action à effectuer lors du chargement du module. Si aucun indicateur n’est spécifié, le comportement de cette fonction est identique à celui de la `AfxLoadLibrary` fonction. Les valeurs possibles de ce paramètre sont décrites dans la documentation [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) .

### <a name="return-value"></a>Valeur renvoyée

Si la fonction est réussie, la valeur de retour est un handle du module. En cas d’échec, la valeur de retour est NULL.

### <a name="remarks"></a>Notes

`AfxLoadLibraryEx` retourne un handle qui peut être utilisé dans [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pour obtenir l’adresse d’une fonction dll. `AfxLoadLibraryEx` peut également être utilisé pour mapper d’autres modules exécutables.

Chaque processus gère un décompte de références pour chaque module de bibliothèque chargé. Ce nombre de références est incrémenté chaque fois `AfxLoadLibraryEx` que est appelé et est décrémenté chaque fois que `AfxFreeLibrary` est appelé. Lorsque le décompte de références atteint zéro, le module n’est pas mappé à partir de l’espace d’adressage du processus appelant et le handle n’est plus valide.

Veillez à utiliser `AfxLoadLibraryEx` et `AfxFreeLibrary` (au lieu des fonctions Win32 `LoadLibraryEx` et `FreeLibrary` ) si votre application utilise plusieurs threads et si elle charge dynamiquement une DLL d’extension MFC. L’utilisation `AfxLoadLibraryEx` de et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la dll d’extension MFC est chargée et déchargée n’endommage pas l’état global des MFC.

L’utilisation `AfxLoadLibraryEx` de dans une application vous oblige à établir une liaison dynamique à la version DLL de MFC. Le fichier d’en-tête pour `AfxLoadLibraryEx` , Afxdll_. h, est inclus uniquement si MFC est lié à l’application en tant que dll. Cette exigence est due à la conception, car vous devez établir une liaison à la version DLL de MFC pour utiliser ou créer des dll d’extension MFC.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdll_. h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager

Pointeur désignant le [Gestionnaire de menus détachements](cmenutearoffmanager-class.md)globaux.

### <a name="syntax"></a>Syntaxe

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmenutearoffmanager. h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a> AfxMouseManager

Pointeur vers le [Gestionnaire de souris](cmousemanager-class.md)global.

### <a name="syntax"></a>Syntaxe

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxmousemanager. h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a> AfxRegisterClass

Utilisez cette fonction pour inscrire des classes de fenêtre dans une DLL qui utilise MFC.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Paramètres

*lpWndClass*\
Pointeur vers une structure [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) contenant des informations sur la classe de fenêtre à inscrire. Pour plus d’informations sur cette structure, consultez la SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la classe est correctement inscrite ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si vous utilisez cette fonction, l’inscription de la classe est automatiquement annulée lorsque la DLL est déchargée.

Dans les builds non-DLL, l' `AfxRegisterClass` identificateur est défini en tant que macro qui est mappée à la fonction Windows `RegisterClass` , car les classes inscrites dans une application sont automatiquement désinscrites. Si vous utilisez `AfxRegisterClass` au lieu de `RegisterClass` , votre code peut être utilisé sans modification dans une application et dans une dll.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a> AfxRegisterWndClass (

Permet d'enregistrer vos propres classes de fenêtre.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Paramètres

*nClassStyle*\
Spécifie le style de classe Windows ou la combinaison de styles créée à l’aide de l’opérateur de bits or (**&#124;**) pour la classe de fenêtre. Pour obtenir la liste des styles de classe, consultez la structure [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) dans le SDK Windows. Si la valeur est NULL, les valeurs par défaut sont définies comme suit :

- Définit le style de la souris sur CS_DBLCLKS, qui envoie des messages de double-clic à la procédure d'affichage lorsque l'utilisateur double-clique sur la souris.

- Définit le style du curseur flèche sur la valeur IDC_ARROW standard Windows.

- Définit le pinceau d’arrière-plan sur NULL, de sorte que la fenêtre n’efface pas son arrière-plan.

- Définit l'icône du logo Windows standard en forme de drapeau flottant.

*hCursor*\
Spécifie un handle pour la ressource curseur à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez la valeur par défaut **0**, vous obtiendrez le curseur de IDC_ARROW standard.

*hbrBackground*\
Spécifie un handle de la ressource pinceau à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez la valeur par défaut **0**, vous obtiendrez un pinceau d’arrière-plan null et, par défaut, votre fenêtre n’effacera pas son arrière-plan lors du traitement des [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

*hIcon*\
Spécifie un handle de la ressource icône à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez la valeur par défaut **0**, vous obtiendrez l’icône de logo Windows standard en drapeau d’ondulation.

### <a name="return-value"></a>Valeur renvoyée

Chaîne de caractères se terminant par null et contenant le nom de la classe. Vous pouvez passer ce nom de classe à la `Create` fonction membre dans `CWnd` ou d’autres classes dérivées de **CWnd**pour créer une fenêtre. Le nom est généré par la bibliothèque MFC.

> [!NOTE]
> La valeur de retour est un pointeur vers une mémoire tampon statique. Pour enregistrer cette chaîne, attribuez-lui une variable `CString`.

### <a name="remarks"></a>Notes

La bibliothèque MFC stocke automatiquement plusieurs classes de fenêtre standard pour vous. Appelez cette fonction si vous souhaitez stocker vos propres classes de fenêtre.

Le nom enregistré pour une classe par `AfxRegisterWndClass` dépend uniquement des paramètres. Si vous appelez `AfxRegisterWndClass` plusieurs fois avec des paramètres identiques, seule une classe lors du premier appel est enregistrée. Les appels ultérieurs à `AfxRegisterWndClass` avec des paramètres identiques retournent la ClassName déjà inscrite.

Si vous appelez `AfxRegisterWndClass` pour plusieurs classes dérivées de CWnd avec des paramètres identiques, au lieu d'obtenir une classe de fenêtre distincte pour chaque classe, chacune partagera la même classe de fenêtre. Ce partage peut entraîner des problèmes si le style de classe CS_CLASSDC est utilisé. Au lieu de plusieurs classes de fenêtre CS_CLASSDC, vous obtenez une seule classe de fenêtre CS_CLASSDC. Toutes les fenêtres C++ qui utilisent cette classe partagent le même contrôleur de périphérique. Pour éviter ce problème, appelez [AfxRegisterClass](#afxregisterclass) pour inscrire la classe.

Reportez-vous à la note technique [TN001 : inscription](../../mfc/tn001-window-class-registration.md) de la classe de fenêtre pour plus d’informations sur l’inscription de la classe de fenêtre et la `AfxRegisterWndClass` fonction.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a> AfxSetPerUserRegistration

Définit si l’application redirige l’accès au registre vers le nœud **HKEY_CURRENT_USER** (**HKCU**).

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*\
dans TRUE indique que les informations du Registre sont dirigées vers le nœud HKCU. FALSe indique que l’application écrit les informations de Registre dans le nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Notes

Avant Windows Vista, les applications qui accédaient au registre utilisaient couramment le nœud **HKEY_CLASSES_ROOT** . Toutefois, avec Windows Vista ou des systèmes d’exploitation ultérieurs, vous devez exécuter une application en mode élevé pour écrire dans HKCR.

Cette méthode permet à votre application de lire et d’écrire dans le registre sans s’exécuter en mode élevé. Il fonctionne en redirigeant l’accès au registre de HKCR vers HKCU. Pour plus d’informations, consultez pages de propriétés de l' [éditeur de liens](../../build/reference/linker-property-pages.md).

Si vous activez la redirection du Registre, le Framework redirige l’accès de HKCR vers **HKEY_CURRENT_USER \Software\Classes**. Seuls les frameworks MFC et ATL sont affectés par la redirection.

L’implémentation par défaut accède au Registre sous HKCR.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxstat_. h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a> AfxSetResourceHandle

Utilisez cette fonction pour définir le handle HINSTANCE qui détermine où les ressources par défaut de l’application sont chargées.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Paramètres

*hInstResource*\
Handle d’instance ou de module vers un. Fichier EXE ou DLL à partir duquel les ressources de l’application sont chargées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a> AfxShellManager

Pointeur vers le [Gestionnaire d’interpréteur](cshellmanager-class.md)de commandes global.

### <a name="syntax"></a>Syntaxe

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxshellmanager. h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a> AfxSocketInit

Appelez cette fonction dans votre `CWinApp::InitInstance` remplacement pour initialiser Windows Sockets.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Paramètres

*lpwsaData*\
Pointeur vers une structure [wsadata,](/windows/win32/api/winsock2/ns-winsock2-wsadata) . Si *lpwsaData* n’est pas égal à null, l’adresse de la `WSADATA` structure est remplie par l’appel à `WSAStartup` . Cette fonction garantit également que `WSACleanup` est appelé pour vous avant la fin de l’application.

### <a name="return-value"></a>Valeur renvoyée

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Lorsque vous utilisez des sockets MFC dans des threads secondaires dans une application MFC liée de manière statique, vous devez appeler `AfxSocketInit` dans chaque thread qui utilise des sockets pour initialiser les bibliothèques de Sockets. Par défaut, `AfxSocketInit` est appelé uniquement dans le thread principal.

### <a name="requirements"></a>Configuration requise

  **En-tête** AfxSock. h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a> AfxUserToolsManager

Pointeur vers le [Gestionnaire des outils utilisateur](cusertoolsmanager-class.md)globaux.

### <a name="syntax"></a>Syntaxe

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxusertoolsmanager. h

## <a name="afxwininit"></a><a name="afxwininit"></a> AfxWinInit

Cette fonction est appelée par la fonction fournie par MFC `WinMain` , dans le cadre de l’initialisation [CWinApp](../../mfc/reference/cwinapp-class.md) d’une application basée sur l’interface graphique utilisateur, pour initialiser MFC.

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Paramètres

*hInstance*\
Handle du module en cours d’exécution.

*hPrevInstance*\
Handle d’une instance précédente de l’application. Pour une application Win32, ce paramètre a toujours la **valeur null**.

*lpCmdLine*\
Pointe vers une chaîne se terminant par un caractère null qui spécifie la ligne de commande pour l’application.

*nCmdShow*\
Spécifie le mode d’affichage de la fenêtre principale d’une application GUI.

### <a name="remarks"></a>Notes

Pour une application console, qui n’utilise pas la fonction fournie par MFC `WinMain` , vous devez appeler `AfxWinInit` directement pour initialiser MFC.

Si vous appelez vous `AfxWinInit` -même, vous devez déclarer une instance d’une `CWinApp` classe. Pour une application console, vous pouvez choisir de ne pas dériver votre propre classe de et d’utiliser à la `CWinApp` place une instance de `CWinApp` directement. Cette technique est appropriée si vous décidez de conserver toutes les fonctionnalités de votre application dans votre implémentation de **main**.

> [!NOTE]
> Lorsqu’il crée un contexte d’activation pour un assembly, MFC utilise une ressource de manifeste fournie par le module User. Le contexte d’activation est créé dans `AfxWinInit` . Pour plus d’informations, consultez [prise en charge des contextes d’activation dans l’état du module MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXWIN. h

## <a name="see-also"></a>Voir aussi

[Macros et globales](mfc-macros-and-globals.md)\
[CWinApp (classe)](cwinapp-class.md)\
[CContextMenuManager, classe](ccontextmenumanager-class.md)\
[CWnd, classe](cwnd-class.md)\
[CFrameWndEx, classe](cframewndex-class.md)\
[CMFCToolBar, classe](cmfctoolbar-class.md)\
[CKeyboardManager, classe](ckeyboardmanager-class.md)\
[CMenuTearOffManager, classe](cmenutearoffmanager-class.md)\
[CMouseManager, classe](cmousemanager-class.md)\
[CShellManager, classe](cshellmanager-class.md)\
[CUserToolsManager, classe](cusertoolsmanager-class.md)
