---
title: Informations sur l’application et la gestion | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ecb761caaeabdd9b4d77f1713bd79a812a3c1a9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952490"
---
# <a name="application-information-and-management"></a>Informations sur l'application et gestion
Lorsque vous écrivez une application, vous créez un seul [CWinApp](../../mfc/reference/cwinapp-class.md)-objet dérivé. Dans certains cas, vous souhaitez obtenir des informations sur cet objet en dehors de la `CWinApp`-objet dérivé. Ou bien, vous devez pouvoir accéder à d’autres objets globaux « gestionnaire ».
  
 La bibliothèque Microsoft Foundation Class fournit les fonctions globales suivantes pour vous aider à accomplir ces tâches :  
  
### <a name="application-information-and-management-functions"></a>Informations sur l’application et les fonctions de gestion  
  
|||  
|-|-|  
|[AfxBeginThread](#afxbeginthread)|Crée un nouveau thread.|  
|[AfxContextMenuManager](#afxcontextmenumanager)|Pointeur vers l’élément global [Gestionnaire de menu de contexte](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Arrête le thread actuel.|  
|[AfxFindResourceHandle](#afxfindresourcehandle)|Parcourt la chaîne de ressource et recherchez un ID de ressource par ressource spécifique et le type de ressource. |
|[AfxFreeLibrary](#afxfreelibrary)|Décrémente le décompte de références du module chargé bibliothèque de liens dynamiques (DLL) ; Lorsque le décompte de références atteint zéro, le module n’est pas mappé.|  
|[AfxGetApp](#afxgetapp)|Retourne un pointeur vers l’application's unique `CWinApp` objet.|  
|[AfxGetAppName](#afxgetappname)|Retourne une chaîne qui contient le nom de l’application.|  
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Retourne un `HINSTANCE` représentant cette instance de l’application.|  
|[AfxGetMainWnd](#afxgetmainwnd)|Retourne un pointeur vers la fenêtre « main » en cours d’une application non-OLE ou de la fenêtre frame en place d’une application serveur.|  
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Utilisez cette fonction pour déterminer si l’application redirige l’accès au Registre vers le **HKEY_CURRENT_USER** ( **HKCU**) nœud.|  
|[AfxGetResourceHandle](#afxgetresourcehandle)|Retourne un `HINSTANCE` à la source de ressources par défaut de l’application. Cela permet d’accéder directement aux ressources de l’application.|  
|[AfxGetThread](#afxgetthread)|Récupère un pointeur vers la version [CWinThread](../../mfc/reference/cwinthread-class.md) objet.|  
|[AfxInitRichEdit](#afxinitrichedit)|Initialise la version 1.0 RichEdit de contrôle pour l’application.|  
|[AfxInitRichEdit2](#afxinitrichedit2)|Initialise la version 2.0 et ultérieures contrôle RichEdit de l’application.| 
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Détermine si la fenêtre donnée est un objet frame étendu.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Détermine si la fenêtre donnée est un objet de barre d’outils.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Pointeur vers l’élément global [Gestionnaire de clavier](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Mappe un module DLL et retourne un handle qui peut être utilisé pour obtenir l’adresse d’une fonction DLL.|  
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Pointeur vers l’élément global [Gestionnaire de menu élément amovible](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Pointeur vers l’élément global [Gestionnaire de souris](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Inscrit une classe de fenêtre dans une DLL qui utilise MFC.|  
|[AfxRegisterWndClass](#afxregisterwndclass)|Inscrit une classe de fenêtre Windows qui complètent celles enregistrées automatiquement par MFC.|  
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Définit si l’application redirige l’accès au Registre vers le **HKEY_CURRENT_USER** ( **HKCU**) nœud.|  
|[AfxSetResourceHandle](#afxsetresourcehandle)|Définit le `HINSTANCE` handle où les ressources par défaut de l’application sont chargés.|  
|[AfxShellManager](#afxshellmanager)|Pointeur vers l’élément global [Gestionnaire de shell](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Appelé dans un `CWinApp::InitInstance` remplacement pour initialiser les Sockets Windows.|  
|[AfxUserToolsManager](#afxusertoolsmanager)|Pointeur vers l’élément global [responsable des outils utilisateur](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Appelée par le fournie par MFC `WinMain` fonction, dans le cadre de la [CWinApp](../../mfc/reference/cwinapp-class.md) l’initialisation d’une application basée sur une interface graphique utilisateur, initialiser les classes MFC. Doit être appelé directement pour les applications de console qui utilisent MFC.|  
  

  
##  <a name="afxbeginthread"></a>  AfxBeginThread  
 Appelez cette fonction pour créer un nouveau thread.  
  
```   
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
 *pfnThreadProc*  
 Pointe vers la fonction de contrôle pour le thread de travail. Ne peut pas être **NULL**. Cette fonction doit être déclarée comme suit :  
  
 `UINT __cdecl MyControllingFunction( LPVOID pParam );`  
  
 *pThreadClass*  
 RUNTIME_CLASS d’un objet dérivé [CWinThread](../../mfc/reference/cwinthread-class.md).  
  
 *pParam*  
 Paramètre à passer à la fonction de contrôle comme indiqué dans le paramètre de la déclaration de fonction dans *pfnThreadProc*.  
  
 *nPriority*  
 La priorité du thread. Pour une liste complète et une description des priorités disponibles, consultez [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) dans le Kit de développement logiciel Windows.  
  
 *nStackSize*  
 Spécifie la taille en octets de la pile pour le nouveau thread. Si 0, la taille de pile par défaut est la même taille de pile en tant que le thread de création.  
  
 *dwCreateFlags*  
 Spécifie un indicateur supplémentaire qui contrôle la création du thread. Cet indicateur peut contenir une des deux valeurs :  
  
- **CREATE_SUSPENDED** démarrage du thread avec un compteur de suspension d’un. Utilisez **CREATE_SUSPENDED** si vous souhaitez initialiser les données de membre de la `CWinThread` de l’objet, tel que [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) ou tous les membres de votre classe dérivée, avant que le thread commence à s’exécuter. Une fois que votre initialisation est terminée, utilisez [CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) pour démarrer le thread en cours d’exécution. Le thread s’exécute pas jusqu'à ce que `CWinThread::ResumeThread` est appelée.  
  
- **0** démarrer le thread immédiatement après sa création.  
  
 *lpSecurityAttrs*  
 Pointe vers un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) structure qui spécifie les attributs de sécurité pour le thread. Si **NULL**, attributs de la même sécurité que le thread de création sera utilisé. Pour plus d’informations sur cette structure, consultez le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’objet thread nouvellement créé, ou **NULL** si une défaillance se produit.  
  
### <a name="remarks"></a>Notes  
 La première forme de `AfxBeginThread` crée un thread de travail. La deuxième forme crée un thread qui peut-être servir comme un thread d’interface utilisateur ou un thread de travail.  
  
 `AfxBeginThread` Crée un nouveau `CWinThread` objet, appelle son [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) pour démarrer l’exécution du thread de fonction et retourne un pointeur vers le thread. Vérifications sont effectuées dans l’ensemble de la procédure pour vous assurer que tous les objets sont libérés correctement n’importe quelle partie de la création échoue. Pour terminer le thread, appelez [AfxEndThread](#afxendthread) à partir de dans le thread ou le retour de la fonction de contrôle du thread de travail.  
  
 Multithreading doit être activé par l’application ; Sinon, cette fonction échoue. Pour plus d’informations sur l’activation de multithreading, reportez-vous à [/MD, / MT, /LD (utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md) sous *Options de compilateur Visual C++*.  
  
 Pour plus d’informations sur `AfxBeginThread`, consultez les articles [Multithreading : création de Threads de travail](../../parallel/multithreading-creating-worker-threads.md) et [Multithreading : création de Threads d’Interface utilisateur](../../parallel/multithreading-creating-user-interface-threads.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  

## <a name="afxcontextmenumanager"></a> AfxContextMenuManager
Pointeur vers l’élément global [Gestionnaire de menu de contexte](ccontextmenumanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CContextMenuManager* afxContextMenuManager;  
```     
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcontextmenumanager.h     

### <a name="see-also"></a>Voir aussi   
 [CContextMenuManager, classe](ccontextmenumanager-class.md)

  
##  <a name="afxendthread"></a>  AfxEndThread  
 Appelez cette fonction pour mettre fin au thread en cours d’exécution.  
  
```   
void AFXAPI AfxEndThread(
    UINT nExitCode,  
    BOOL bDelete  = TRUE); 
```  
  
### <a name="parameters"></a>Paramètres  
 *nExitCode*  
 Spécifie le code de sortie du thread.  
  
 *bDelete*  
 Supprime l’objet thread à partir de la mémoire.  
  
### <a name="remarks"></a>Notes  
 Doit être appelée depuis le thread peut être interrompue.  
  
 Pour plus d’informations sur `AfxEndThread`, consultez l’article [Multithreading : arrêt de Threads](../../parallel/multithreading-terminating-threads.md).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Utilisez `AfxFindResourceHandle` pour parcourir la chaîne de ressource et localiser un type d’ID et de ressources spécifique par la ressource.  
   
### <a name="syntax"></a>Syntaxe    
```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );  
```
### <a name="parameters"></a>Paramètres  
 *Caractère*  
 Un pointeur vers une chaîne contenant l’ID de ressource.    
 *lpszType*  
 Pointeur vers le type de ressource. Pour obtenir la liste des types de ressources, consultez [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) dans le Kit de développement logiciel Windows.  
   
### <a name="return-value"></a>Valeur de retour  
 Handle vers le module qui contient la ressource.  
   
### <a name="remarks"></a>Notes  
 `AfxFindResourceHandle` recherche de la ressource spécifique et retourne un handle vers le module qui contient la ressource. La ressource peut être dans n’importe quel vous avez chargé des DLL d’extension MFC. `AfxFindResourceHandle` vous indique à lequel d'entre eux contient la ressource.  
  
 Les modules sont recherchées dans cet ordre :  
  
1.  Le module principal (s’il est une DLL d’extension MFC).  
  
2.  Modules non système.  
  
3.  Modules linguistiques.  
  
4.  Le module principal (s’il est une DLL système).  
  
5.  Modules système.  
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
  
##  <a name="afxfreelibrary"></a>  AfxFreeLibrary  
 Les deux `AfxFreeLibrary` et `AfxLoadLibrary` conserver un décompte de références pour chaque module chargé de bibliothèque.  
  
```   
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib); 
```  
  
### <a name="parameters"></a>Paramètres  
 *hInstLib*  
 Handle du module chargé de bibliothèque. [AfxLoadLibrary](#afxloadlibrary) retourne ce handle.  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si la fonction réussit ; sinon, **FALSE**.  
  
### <a name="remarks"></a>Notes  
 `AfxFreeLibrary` Décrémente le décompte de références du module chargé bibliothèque de liens dynamiques (DLL). Lorsque le décompte de références atteint zéro, le module n’est pas mappé à partir de l’espace d’adressage du processus appelant et le handle n’est plus valide. Ce nombre de références est incrémenté chaque fois que `AfxLoadLibrary` est appelée.  
  
 Avant l’annulation du mappage d’un module de bibliothèque, le système permet à la DLL détacher les processus. Cela permet à la DLL pour nettoyer les ressources allouées pour le compte du processus en cours. Une fois que la fonction de point d’entrée retourne, le module de bibliothèque est supprimé de l’espace d’adressage du processus actuel.  
  
 Utilisez `AfxLoadLibrary` pour mapper un module DLL.  
  
 Veillez à utiliser `AfxFreeLibrary` et `AfxLoadLibrary` (au lieu des fonctions Win32 `FreeLibrary` et `LoadLibrary`) si votre application utilise plusieurs threads. À l’aide de `AfxLoadLibrary` et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la DLL est chargé et déchargé d’extension MFC n’altère pas l’état global des MFC.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [AfxLoadLibrary](#afxloadlibrary).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdll_.h  
  
##  <a name="afxgetapp"></a>  AfxGetApp  
 Le pointeur retourné par cette fonction peut être utilisé pour accéder aux informations d’application telles que le code de la distribution du message principal ou de la fenêtre au premier plan.  
  
```   
CWinApp* AFXAPI AfxGetApp(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le seul `CWinApp` objet pour l’application.  
  
### <a name="remarks"></a>Notes  
 Si cette méthode retourne la valeur NULL, cela peut indiquer que la fenêtre principale de l’application n'a pas été entièrement initialisée encore. Il peut également indiquer un problème.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxgetappname"></a>  AfxGetAppName  
 La chaîne retournée par cette fonction peut être utilisée pour les messages de diagnostic ou en tant que racine pour les noms de chaîne temporaire.  
  
```   
LPCTSTR AFXAPI AfxGetAppName(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Chaîne terminée par le caractère null qui contient le nom de l’application.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxgetinstancehandle"></a>  AfxGetInstanceHandle  
 Cette fonction vous permet de récupérer le handle d’instance de l’application actuelle.  
  
```   
HINSTANCE  AFXAPI AfxGetInstanceHandle(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `HINSTANCE` à l’instance actuelle de l’application. Si l’appelé à partir d’une DLL liée à la version USRDLL de MFC, un `HINSTANCE` à la DLL est retournée.  
  
### <a name="remarks"></a>Notes  
 `AfxGetInstanceHandle` Retourne toujours la `HINSTANCE` de votre fichier exécutable (. (EXE), sauf si elle est appelée à partir d’une DLL liée avec la version USRDLL de MFC. Dans ce cas, elle retourne un `HINSTANCE` à la DLL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxgetmainwnd"></a>  AfxGetMainWnd  
 Si votre application est un serveur OLE, appelez cette fonction pour récupérer un pointeur vers la fenêtre principale active de l’application plutôt que directement référence à la [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) membre de l’objet application.  
  
```   
CWnd* AFXAPI AfxGetMainWnd(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si le serveur dispose d’un objet qui est en place active à l’intérieur d’un conteneur et ce conteneur est actif, cette fonction retourne un pointeur vers l’objet de fenêtre frame qui contient le document actif sur place.  
  
 Si aucun objet qui est actif en place dans un conteneur, ou votre application n’est pas un serveur OLE, cette fonction retourne simplement le *m_pMainWnd* de votre objet application.  
  
 Si `AfxGetMainWnd` est appelée à partir du thread principal de l’application, elle retourne la fenêtre principale de l’application selon les règles ci-dessus. Si la fonction est appelée à partir d’un thread secondaire dans l’application, la fonction retourne la fenêtre principale associée au thread qui a effectué l’appel.  
  
### <a name="remarks"></a>Notes  
 Si votre application n’est pas un serveur OLE, appel de cette fonction est équivalent à la référence directe à la *m_pMainWnd* membre de votre objet application.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxgetperuserregistration"></a>  AfxGetPerUserRegistration  
 Utilisez cette fonction pour déterminer si l’application redirige l’accès au Registre vers le **HKEY_CURRENT_USER** ( **HKCU**) nœud.  
  
```  
BOOL AFXAPI AfxGetPerUserRegistration();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Indique que les informations du Registre sont dirigées vers le **HKCU** nœud ; `FALSE` indique que l’application écrit les informations du Registre dans le nœud par défaut. Le nœud de la valeur par défaut est **HKEY_CLASSES_ROOT** ( **HKCR**).  
  
### <a name="remarks"></a>Notes  
 Si vous activez la redirection du Registre, le framework redirige l’accès à partir de **HKCR** à **HKEY_CURRENT_USER\Software\Classes**. Seuls les infrastructures de MFC et ATL sont affectés par la redirection.  
  
 Pour modifier si l’application redirige l’accès au Registre, utilisez [AfxSetPerUserRegistration](#afxsetperuserregistration).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxstat_.h    
  
##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle  
 Utilisez le `HINSTANCE` handle retourné par cette fonction pour accéder aux ressources de l’application directement, par exemple, dans les appels à la fonction `FindResource`.  
  
```   
extern HINSTANCE  AfxGetResourceHandle(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `HINSTANCE` handle où les ressources par défaut de l’application sont chargés.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxgetthread"></a>  AfxGetThread  
 Appelez cette fonction pour obtenir un pointeur vers le [CWinThread](../../mfc/reference/cwinthread-class.md) objet qui représente le thread en cours d’exécution.  
  
```   
CWinThread* AfxGetThread(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le thread en cours d’exécution ; dans le cas contraire **NULL**.  
  
### <a name="remarks"></a>Notes  
 Doit être appelée depuis le thread souhaité.  
  
> [!NOTE]
>  Si vous déplacez un appel de projet MFC `AfxGetThread` à partir de versions de Visual C++ 4.2, 5.0 ou 6.0, `AfxGetThread` appelle [AfxGetApp](#afxgetapp) si aucun thread n’est trouvée. Dans les versions plus récentes du compilateur, `AfxGetThread` retourne **NULL** si aucun thread n’a été trouvée. Si vous souhaitez que le thread d’application, vous devez appeler `AfxGetApp`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxinitrichedit"></a>  AfxInitRichEdit  
 Appelez cette fonction pour initialiser le contrôle RichEdit (version 1.0) pour l’application.  
  
```   
BOOL AFXAPI AfxInitRichEdit(); 
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction est fournie pour la compatibilité descendante. Nouvelles applications doivent utiliser [AfxInitRichEdit2](#afxinitrichedit2).  
  
 `AfxInitRichEdit` charge RICHED32. DLL d’initialisation de la version 1.0 du contrôle RichEdit. Pour utiliser les versions 2.0 et 3.0 du contrôle RichEdit, RICHED20. DLL doit être chargé. Cela est accompli par un appel à [AfxInitRichEdit2](#afxinitrichedit2).  
  
 Pour mettre à jour les contrôles RichEdit dans les applications Visual C++ existantes vers la version 2.0, ouvrez le. Fichier RC sous forme de texte, modifiez le nom de classe de chaque contrôle RichEdit de « RICHEDIT » à « RichEdit20a ». Puis remplacez l’appel à `AfxInitRichEdit` avec `AfxInitRichEdit2`.  
  
 Cette fonction initialise également la bibliothèque de contrôles communs, si la bibliothèque n’a pas déjà été initialisée pour le processus. Si vous utilisez le contrôle d’édition enrichi directement à partir de votre application MFC, vous devez appeler cette fonction pour vous assurer que MFC a correctement initialisé à l’exécution du contrôle RichEdit. Si vous appelez la méthode Create de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), ou [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), vous ne devez généralement appeler cette fonction, mais dans certains cas, il peut être nécessaire.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxinitrichedit2"></a>  AfxInitRichEdit2  
 Appelez cette fonction pour initialiser le contrôle RichEdit (version 2.0 et ultérieur) pour l’application.  
  
```   
BOOL AFXAPI AfxInitRichEdit2(); 
```  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour charger le RICHED20. Contrôle d’édition DLL et initialiser la version 2.0 de la riche. Si vous appelez la méthode Create de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), ou [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), vous ne devez généralement appeler cette fonction, mais dans certains cas, il peut être nécessaire.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  

  ## <a name="afxisextendedframeclass"></a>  AfxIsExtendedFrameClass
Détermine si la fenêtre donnée est un objet frame étendu.  
   
### <a name="syntax"></a>Syntaxe    
```  
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );  
```
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
 Pointeur vers un objet dérivé de `CWnd`.  
   
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la fenêtre fournie est un objet frame étendu ; dans le cas contraire `FALSE`.  
   
### <a name="remarks"></a>Notes  
 Cette méthode retourne `TRUE` si `pWnd` dérive de l’une des classes suivantes :  
  
-   `CFrameWndEx`  
  
-   `CMDIFrameWndEx`  
  
-   `COleIPFrameWndEx`  
  
-   `COleDocIPFrameWndEx`  
  
-   `CMDIChildWndEx`  
  
 Cette méthode est utile quand vous devez valider le fait qu’un paramètre de fonction ou de méthode est une fenêtre frame étendue.  
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxpriv.h  
   
### <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](cwnd-class.md)   
 [CFrameWndEx, classe](cframewndex-class.md)   

## <a name="afxismfctoolbar"></a> AfxIsMFCToolBar
Détermine si la fenêtre donnée est un objet de barre d’outils.  
   
### <a name="syntax"></a>Syntaxe    
```  
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);  
```
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
 Pointeur vers un objet dérivé de `CWnd`.  
   
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la fenêtre fournie est un objet de la barre d’outils ; dans le cas contraire `FALSE`.  
   
### <a name="remarks"></a>Notes  
 Cette méthode retourne `TRUE` si *pWnd* dérive `CMFCToolBar`. Cette méthode est utile lorsque vous devez valider qu’un paramètre de fonction ou une méthode est un `CMFCToolBar` objet.  
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxpriv.h  
   
### <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](cwnd-class.md)   
 [CMFCToolBar, classe](cmfctoolbar-class.md)

 
## <a name="afxkeyboardmanager"></a> AfxKeyboardManager
Pointeur vers l’élément global [Gestionnaire de clavier](ckeyboardmanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CKeyboardManager* afxKeyboardManager;  
```  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxkeyboardmanager.h  
   
### <a name="see-also"></a>Voir aussi  

 [Macros, fonctions globales et Variables globales](mfc-macros-and-globals.md)   
 [CKeyboardManager, classe](ckeyboardmanager-class.md)


##  <a name="afxloadlibrary"></a>  AfxLoadLibrary  
 Utilisez `AfxLoadLibrary` pour mapper un module DLL.  
  
```   
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName); 
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszModuleName*  
 Pointe vers une chaîne terminée par le caractère null qui contient le nom du module (soit un. DLL ou. Fichier EXE). Le nom spécifié est le nom de fichier du module.  
  
 Si la chaîne spécifie un chemin d’accès, mais le fichier n’existe pas dans le répertoire spécifié, la fonction échoue.  
  
 Si un chemin d’accès n’est pas spécifié et que l’extension de nom de fichier est omise, l’extension par défaut. DLL est ajouté. Toutefois, la chaîne de nom de fichier peut inclure un caractère de point de fin (.) pour indiquer que le nom du module n’a aucune extension. Si aucun chemin d’accès n’est spécifié, la fonction recherche le fichier dans l’ordre suivant :  
  
-   Le répertoire à partir duquel l’application chargée.  
  
-   Le répertoire actif.  
  
- **Windows 95/98 :** le répertoire système Windows. **Windows NT :** le répertoire de système de Windows 32 bits. Le nom de ce répertoire est SYSTEM32.  
  
- **Windows NT uniquement :** répertoire du système Windows le 16 bits. Aucune fonction Win32 qui permet d’obtenir le chemin d’accès de ce répertoire, mais il est recherché. Le nom de ce répertoire est système.  
  
-   Le répertoire Windows.  
  
-   Les répertoires qui sont répertoriés dans la variable d’environnement PATH.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est un handle vers le module. Si la fonction échoue, la valeur de retour est NULL.  
  
### <a name="remarks"></a>Notes  
 Elle retourne un handle qui peut être utilisé dans [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) pour obtenir l’adresse d’une fonction DLL. `AfxLoadLibrary` peut également être utilisé pour mapper d’autres modules exécutables.  
  
 Chaque processus conserve un décompte de références pour chaque module chargé de bibliothèque. Ce nombre de références est incrémenté à chaque `AfxLoadLibrary` est appelée et est décrémenté à chaque fois `AfxFreeLibrary` est appelée. Lorsque le décompte de références atteint zéro, le module n’est pas mappé à partir de l’espace d’adressage du processus appelant et le handle n’est plus valide.  
  
 Veillez à utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions Win32 `LoadLibrary` et `FreeLibrary`) si votre application utilise plusieurs threads et s’il charge dynamiquement une DLL d’extension MFC. À l’aide de `AfxLoadLibrary` et `AfxFreeLibrary` permet de s’assurer que le code de démarrage et d’arrêt qui s’exécute lorsque la DLL d’extension MFC est chargé et déchargé n’altère pas l’état global des MFC.  
  
 À l’aide de `AfxLoadLibrary` dans une application nécessite que vous liez dynamiquement à la version DLL de MFC ; le fichier d’en-tête pour `AfxLoadLibrary`, Afxdll_.h, est uniquement inclus si MFC est lié à l’application en tant que DLL. Ceci est normal, car vous devez créer un lien vers la version DLL de MFC à utiliser ou créer des DLL d’extension MFC.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdll_.h  
   
## <a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager
Pointeur vers l’élément global [Gestionnaire de menu élément amovible](cmenutearoffmanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CMenuTearOffManager* g_pTearOffMenuManager;  
```  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxmenutearoffmanager.h  
   
### <a name="see-also"></a>Voir aussi     
 [CMenuTearOffManager, classe](cmenutearoffmanager-class.md)
 
## <a name="afxmousemanager"></a>  AfxMouseManager
Pointeur vers l’élément global [Gestionnaire de souris](cmousemanager-class.md).  
   
### <a name="syntax"></a>Syntaxe  
  ```  
CMouseManager* afxMouseManager;  
```  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxmousemanager.h  
   
### <a name="see-also"></a>Voir aussi  
 [CMouseManager, classe](cmousemanager-class.md)
 

  
##  <a name="afxregisterclass"></a>  AfxRegisterClass  
 Utilisez cette fonction pour inscrire des classes de fenêtre dans une DLL qui utilise MFC.  
  
```   
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass); 
```  
  
### <a name="parameters"></a>Paramètres  
 *lpWndClass*  
 Pointeur vers un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) structure contenant des informations sur la classe de fenêtre à inscrire. Pour plus d’informations sur cette structure, consultez le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si la classe est correctement inscrite ; sinon **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Si vous utilisez cette fonction, la classe est automatiquement annulée lorsque la DLL est déchargée.  
  
 Dans les versions de DLL non-le `AfxRegisterClass` identificateur est défini comme une macro mappée à la fonction `RegisterClass`, étant donné que les classes inscrits dans une application sont automatiquement annulées. Si vous utilisez `AfxRegisterClass` au lieu de `RegisterClass`, votre code peut être utilisé sans modification dans une application et dans une DLL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxregisterwndclass"></a>  AfxRegisterWndClass  
 Permet d'enregistrer vos propres classes de fenêtre.  
  
```  
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,  
    HCURSOR hCursor = 0,  
    HBRUSH hbrBackground = 0,  
    HICON hIcon = 0);  
```  
  
### <a name="parameters"></a>Paramètres  
 *nClassStyle*  
 Spécifie le style de classe Windows ou une combinaison des styles, créée à l’aide de l’opération de bits OR ( **&#124;**) (opérateur), pour la classe de fenêtre. Pour obtenir la liste des styles de classe, consultez la [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) structure dans le SDK Windows. Si **NULL**, les valeurs par défaut seront définies comme suit :  
  
-   Définit le style de la souris sur **CS_DBLCLKS**, qui envoie des messages à la procédure de fenêtre de double quand l’utilisateur double-clique sur la souris.  
  
-   Définit le style du curseur flèche vers le Windows standard **IDC_ARROW**.  
  
-   Définit le pinceau d’arrière-plan **NULL**, de sorte que la fenêtre n’efface pas son arrière-plan.  
  
-   Définit l'icône du logo Windows standard en forme de drapeau flottant.  
  
 *hCursor*  
 Spécifie un handle pour la ressource curseur à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez la valeur par défaut de **0**, vous obtenez la norme **IDC_ARROW** curseur.  
  
 *hbrBackground*  
 Spécifie un handle de la ressource pinceau à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez la valeur par défaut de **0**, vous aurez un **NULL** pinceau d’arrière-plan et votre fenêtre, par défaut, n’effacement pas son arrière-plan lors du traitement de [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055).  
  
 *hIcon*  
 Spécifie un handle de la ressource icône à installer dans chaque fenêtre créée à partir de la classe de fenêtre. Si vous utilisez la valeur par défaut de **0**, vous obtiendrez l’icône du logo Windows standard, drapeau.  
  
### <a name="return-value"></a>Valeur de retour  
 Chaîne de caractères se terminant par null et contenant le nom de la classe. Vous pouvez passer ce nom de classe pour le `Create` fonction membre dans `CWnd` ou autres **CWnd**classes dérivées pour créer une fenêtre. Le nom est généré par la bibliothèque MFC.  
  
> [!NOTE]
>  La valeur de retour est un pointeur vers une mémoire tampon statique. Pour enregistrer cette chaîne, attribuez-lui une variable `CString`.  
  
### <a name="remarks"></a>Notes  
 La bibliothèque MFC stocke automatiquement plusieurs classes de fenêtre standard pour vous. Appelez cette fonction si vous souhaitez stocker vos propres classes de fenêtre.  
  
 Le nom enregistré pour une classe par `AfxRegisterWndClass` dépend uniquement des paramètres. Si vous appelez `AfxRegisterWndClass` plusieurs fois avec des paramètres identiques, seule une classe lors du premier appel est enregistrée. Les appels suivants à `AfxRegisterWndClass` avec des paramètres identiques retournent simplement le nom de la classe déjà enregistrée.  
  
 Si vous appelez `AfxRegisterWndClass` pour plusieurs classes dérivées de CWnd avec des paramètres identiques, au lieu d'obtenir une classe de fenêtre distincte pour chaque classe, chacune partagera la même classe de fenêtre. Cela peut entraîner des problèmes si le **CS_CLASSDC** style de classe est utilisée. Au lieu de plusieurs **CS_CLASSDC** classes de fenêtre, vous vous retrouvez avec une **CS_CLASSDC** classe de fenêtre et toutes les fenêtres C++ qui utilisent la classe partageront le même contrôleur de domaine. Pour éviter ce problème, appelez [AfxRegisterClass](#afxregisterclass) pour inscrire la classe.  
  
 Reportez-vous à la Note technique [TN001 : inscription de classe](../../mfc/tn001-window-class-registration.md) pour plus d’informations sur l’inscription de classe de fenêtre et la `AfxRegisterWndClass` (fonction).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
  
##  <a name="afxsetperuserregistration"></a>  AfxSetPerUserRegistration  
 Définit si l’application redirige l’accès au Registre vers le **HKEY_CURRENT_USER** ( **HKCU**) nœud.  
  
```  
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bActivez*  
 `TRUE` Indique que les informations du Registre sont dirigées vers le **HKCU** nœud ; `FALSE` indique que l’application écrit les informations du Registre dans le nœud par défaut. Le nœud de la valeur par défaut est **HKEY_CLASSES_ROOT** ( **HKCR**).  
  
### <a name="remarks"></a>Notes  

Avant Windows Vista, les applications qui ont accédé le Registre, généralement le **HKEY_CLASSES_ROOT** nœud. Toutefois, avec Windows Vista ou versions ultérieures, vous devez exécuter une application en mode élevé pour écrire dans **HKCR**.  
  
 Cette méthode permet à votre application lire et écrire dans le Registre sans exécuter en mode élevé en redirigeant l’accès au Registre à partir de **HKCR** à **HKCU**. Pour plus d’informations, consultez [les Pages de propriétés de l’éditeur de liens](../../ide/linker-property-pages.md).  
  
 Si vous activez la redirection du Registre, le framework redirige l’accès à partir de **HKCR** à **HKEY_CURRENT_USER\Software\Classes**. Seuls les infrastructures de MFC et ATL sont affectés par la redirection.  
  
 L’implémentation par défaut accède au Registre sous **HKCR**.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxstat_.h    
  
##  <a name="afxsetresourcehandle"></a>  AfxSetResourceHandle  
 Cette fonction permet de définir la `HINSTANCE` handle qui détermine où les ressources par défaut de l’application sont chargés.  
  
```  
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);  
```  
  
### <a name="parameters"></a>Paramètres  
 *hInstResource*  
 Le handle d’instance ou un module à un. Fichier EXE ou DLL à partir de laquelle les ressources de l’application sont chargés.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  

## <a name="afxshellmanager"></a>  AfxShellManager
Pointeur vers l’élément global [Gestionnaire de shell](cshellmanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CShellManager* afxShellManager;  
```  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxshellmanager.h  
   
### <a name="see-also"></a>Voir aussi  
 [CShellManager, classe](cshellmanager-class.md)
  
##  <a name="afxsocketinit"></a>  AfxSocketInit  
 Appelez cette fonction dans votre `CWinApp::InitInstance` remplacement pour initialiser les Sockets Windows.  
  
```  
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpwsaData*  
 Un pointeur vers un [WSADATA](../../mfc/reference/wsadata-structure.md) structure. Si *lpwsaData* n’est pas égal à `NULL`, puis l’adresse de la `WSADATA` structure est remplie par l’appel à `WSAStartup`. Cette fonction garantit également que `WSACleanup` est appelé automatiquement avant l’arrêt de l’application.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Lors de l’utilisation de sockets MFC dans les threads secondaires dans une application MFC liée de manière statique, vous devez appeler `AfxSocketInit` dans chaque thread qui utilise des sockets pour initialiser les bibliothèques de socket. Par défaut, `AfxSocketInit` est appelée uniquement dans le thread principal.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxsock.h  

## <a name="afxusertoolsmanager"></a>  AfxUserToolsManager
Pointeur vers l’élément global [responsable des outils utilisateur](cusertoolsmanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CUserToolsManager* afxUserToolsManager;  
```  
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxusertoolsmanager.h  
   
### <a name="see-also"></a>Voir aussi  
 [CUserToolsManager, classe](cusertoolsmanager-class.md)
 
  
##  <a name="afxwininit"></a>  AfxWinInit  
 Cette fonction est appelée par le fournie par MFC `WinMain` fonction, dans le cadre de la [CWinApp](../../mfc/reference/cwinapp-class.md) l’initialisation d’une application basée sur une interface graphique utilisateur, initialiser les classes MFC.  
  
```  
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,  
    HINSTANCE hPrevInstance,  
    LPTSTR lpCmdLine,  
    int nCmdShow);  
```  
  
### <a name="parameters"></a>Paramètres  
 *hInstance*  
 Le handle du module en cours d’exécution.  
  
 *hPrevInstance*  
 Handle vers une instance précédente de l’application. Pour une application Win32, ce paramètre est toujours **NULL**.  
  
 *lpCmdLine*  
 Pointe vers une chaîne se terminant par null spécifiant la ligne de commande pour l’application.  
  
 *nCmdShow*  
 Spécifie la façon dont la fenêtre principale d’une application d’interface graphique utilisateur sont affichée.  
  
### <a name="remarks"></a>Notes  
 Pour une application console, qui n’utilisent pas dans les MFC fournie `WinMain` (fonction), vous devez appeler `AfxWinInit` directement pour initialiser les classes MFC.  
  
 Si vous appelez `AfxWinInit` vous-même, vous devez déclarer une instance d’un `CWinApp` classe. Pour une application console, vous pouvez choisissez de ne pas dériver votre propre classe de `CWinApp` et à la place utiliser une instance de `CWinApp` directement. Cette technique est appropriée si vous décidez de conserver toutes les fonctionnalités de votre application dans votre implémentation de **principal**.  
  
> [!NOTE]
>  Lorsqu’il crée un contexte d’activation pour un assembly, MFC utilise une ressource de manifeste fournie par le module de l’utilisateur. Le contexte d’activation est créé dans `AfxWinInit`. Pour plus d’informations, consultez [prise en charge des contextes d’Activation dans l’état du Module MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]  

### <a name="requirements"></a>Configuration requise  
  **En-tête** afxwin.h  
    
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)   
 [CWinApp, classe](../../mfc/reference/cwinapp-class.md)
