---
title: DLL et le comportement de la bibliothèque d’exécution Visual C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: feee3d888fbf43bfd8675ccc83a04fd4e1f0b528
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392060"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLL et le comportement de la bibliothèque d’exécution Visual C++  
  
Lorsque vous générez une bibliothèque de liens dynamiques (DLL) à l’aide de Visual C++, par défaut, l’éditeur de liens inclut la bibliothèque d’exécution Visual C++ (VCRuntime). VCRuntime contient le code requis pour l’initialisation et de fin d’un fichier exécutable C/C++. Quand liées dans une DLL, le code VCRuntime fournit une fonction de point d’entrée DLL interne appelée `_DllMainCRTStartup` qui gère les messages de système d’exploitation Windows à la DLL à attacher ou détacher un processus ou thread. Le `_DllMainCRTStartup` fonction effectue les tâches essentielles, telles que la sécurité de mémoire tampon de pile configuré, l’initialisation de C Runtime library (CRT) et l’arrêt et appelle à des constructeurs et les destructeurs des objets statiques et globales. `_DllMainCRTStartup` appelle de raccordement également des fonctions pour les autres bibliothèques telles que WinRT, MFC et ATL pour effectuer leurs propres l’initialisation et l’arrêt. Sans cette initialisation, la bibliothèque CRT et autres bibliothèques, ainsi que des variables statiques, serait un état non initialisé. Les routines de fin et le même initialisation interne VCRuntime sont appelées si votre DLL utilise un CRT lié de manière statique ou une DLL de bibliothèque CRT liée dynamiquement.  
  
## <a name="default-dll-entry-point-dllmaincrtstartup"></a>Par défaut _DllMainCRTStartup de point d’entrée DLL  
  
Dans Windows, toutes les DLL peuvent contenir une fonction de point d’entrée facultative, généralement appelée `DllMain`, qui est appelée pour l’initialisation et de fin. Cela vous donne la possibilité d’allouer ou de libérer des ressources supplémentaires en fonction des besoins. Windows appelle la fonction de point d’entrée dans quatre cas : attacher un processus, détacher un processus, attachement et détachement de thread. Lorsqu’une DLL est chargée dans un espace d’adressage de processus, lors du chargée d’une application qui l’utilise, ou lorsque l’application demande la DLL lors de l’exécution, le système d’exploitation crée une copie distincte des données de la DLL. Il s’agit *attacher un processus*. *Attachement de thread* se produit lorsque le processus de chargement de la DLL en crée un nouveau thread. *Détachement de thread* se produit lorsque le thread s’arrête, et *détacher un processus* est lors de la DLL n’est plus nécessaire et est publiée par une application. Le système d’exploitation effectue un appel distinct pour le point d’entrée DLL pour chacun de ces événements, en passant un *raison* argument pour chaque type d’événement. Par exemple, le système d’exploitation envoie `DLL_PROCESS_ATTACH` comme le *raison* argument afin de signaler le processus à attacher.  
  
La bibliothèque VCRuntime fournit une fonction de point d’entrée appelée `_DllMainCRTStartup` pour gérer les opérations d’initialisation et d’arrêt par défaut. Sur le processus d’attachement, le `_DllMainCRTStartup` fonction définit des vérifications de sécurité des mémoires tampons, initialise le CRT et autres bibliothèques, initialise les informations de type au moment de l’exécution, initialise et appelle les constructeurs pour les données statiques et non local, initialise le stockage local des threads , incrémente un compteur interne statique pour chaque attacher, puis appelle une fournie par l’utilisateur ou bibliothèque- `DllMain`. Sur le processus de détachement, la fonction effectue les étapes dans l’ordre inverse. Il appelle `DllMain`, décrémente le compteur interne, appelle des destructeurs, arrêt des appels CRT, fonctions et inscrit `atexit` fonctions et notifie les autres bibliothèques d’arrêt. Lorsque le compteur de pièce jointe est envoyé à zéro, la fonction retourne `FALSE` pour indiquer à Windows que la DLL peut être déchargée. Le `_DllMainCRTStartup` est également appelée au cours de la thread attachement et détachement de thread. Dans ce cas, le code VCRuntime n’aucune initialisation supplémentaire ou l’arrêt de sa propre et appelle simplement `DllMain` pour transmettre le message. Si `DllMain` retourne `FALSE` processus attacher, signaler l’échec, `_DllMainCRTStartup` appelle `DllMain` à nouveau et passe `DLL_PROCESS_DETACH` en tant que le *raison* argument, puis passe à travers le reste de la processus d’arrêt.  
  
Lorsque vous générez des DLL dans Visual C++, le point d’entrée par défaut `_DllMainCRTStartup` fournie par VCRuntime est liée automatiquement. Vous n’avez pas besoin de spécifier une fonction de point d’entrée pour votre DLL à l’aide de la [/ENTRY (symbole de point d’entrée)](../build/reference/entry-entry-point-symbol.md) option de l’éditeur de liens.  
  
> [!NOTE]
> Bien qu’il soit possible de spécifier une autre fonction de point d’entrée pour une DLL à l’aide de /ENTRY : option de l’éditeur de liens, nous ne recommandons pas, car la fonction de point d’entrée aurait à dupliquer tout ce qui `_DllMainCRTStartup` est le cas, dans le même ordre. Le VCRuntime fournit des fonctions qui vous permettent de dupliquer son comportement. Par exemple, vous pouvez appeler [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) immédiatement sur le processus d’attachement pour prendre en charge la [/GS (vérification de sécurité de mémoire tampon)](../build/reference/gs-buffer-security-check.md) mémoire tampon de l’option de vérification. Vous pouvez appeler la `_CRT_INIT` fonction, en passant les mêmes paramètres que la fonction de point d’entrée, pour effectuer le reste des fonctions DLL l’initialisation ou l’arrêt.  
  
<a name="initializing-a-dll"></a>  
  
## <a name="initialize-a-dll"></a>Initialiser une DLL  
  
Votre DLL peut avoir le code d’initialisation qui doit s’exécuter lorsque le chargement de la DLL. Dans l’ordre pour vous permet d’effectuer vos propres fonctions d’initialisation et l’arrêt de DLL, `_DllMainCRTStartup` appelle une fonction appelée `DllMain` que vous pouvez fournir. Votre `DllMain` doit avoir la signature requise pour un point d’entrée DLL. La fonction de point d’entrée par défaut `_DllMainCRTStartup` appelle `DllMain` en utilisant les mêmes paramètres transmis par Windows. Par défaut, si vous ne fournissez pas un `DllMain` (fonction), Visual C++ fournit une pour vous et le lie dans afin que `_DllMainCRTStartup` a toujours quelque chose à appeler. Cela signifie que si vous n’avez pas besoin d’initialiser la DLL, il est rien de spécial, que vous devez effectuer lors de la génération de votre DLL.  
  
C’est la signature utilisée pour `DllMain`:  
  
```cpp  
#include <windows.h>  
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```  
  
Certaines bibliothèques encapsulent la `DllMain` fonction pour vous. Par exemple, dans une DLL MFC standard, implémentent la `CWinApp` l’objet `InitInstance` et `ExitInstance` des fonctions membres pour effectuer l’initialisation et arrêt requises par votre DLL. Pour plus d’informations, consultez la [initialiser regular des DLL MFC](#initializing-regular-dlls) section.  
  
> [!WARNING]
> Il existe des limites importantes sur ce que vous pouvez faire en toute sécurité dans un point d’entrée DLL. Consultez [meilleures pratiques générales](https://msdn.microsoft.com/library/windows/desktop/dn633971#general_best_practices) d’API Windows spécifiques qui sont risqué d’appeler `DllMain`. Si vous avez besoin n’est pas défini, mais l’initialisation de la plus simple puis le faire dans une fonction d’initialisation pour la DLL. Vous pouvez exiger des applications d’appeler la fonction d’initialisation après `DllMain` a exécution et avant qu’ils appellent de toutes les autres fonctions dans la DLL.  
  
<a name="initializing-non-mfc-dlls"></a>  
  
### <a name="initialize-ordinary-non-mfc-dlls"></a>Initialiser les DLL ordinaires (non-MFC)  
  
Pour effectuer votre propre initialisation dans les DLL ordinaires (non-MFC) qui utilisent l’objet fourni par le VCRuntime `_DllMainCRTStartup` point d’entrée, votre code source de la DLL doit contenir une fonction appelée `DllMain`. Le code suivant présente une structure de base indiquant quelles la définition de `DllMain` peut ressembler à :  
  
```cpp  
#include <windows.h>
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason) 
    { 
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```  
  
> [!NOTE]
> Documentation du Kit de développement logiciel Windows plus anciens indique que le nom réel de la fonction de point d’entrée DLL doit être spécifié sur l’éditeur de liens de la ligne de commande avec l’option /ENTRY. Avec Visual C++, vous n’avez pas besoin d’utiliser l’option /ENTRY si le nom de votre fonction de point d’entrée est `DllMain`. En fait, si vous utilisez l’option /ENTRY et le nom de votre point d’entrée de fonction quelque chose autres que `DllMain`, la bibliothèque CRT ne pas initialisée correctement, sauf si votre fonction de point d’entrée appelle la même initialisation qui `_DllMainCRTStartup` rend.  
  
<a name="initializing-regular-dlls"></a>  
  
### <a name="initialize-regular-mfc-dlls"></a>Initialiser des DLL régulière MFC  
  
Étant donné que les DLL régulières MFC ont un `CWinApp` de l’objet, ils doivent effectuer leurs tâches d’initialisation et d’arrêt dans le même emplacement qu’une application MFC : dans le `InitInstance` et `ExitInstance` les fonctions membres de la DLL `CWinApp`-dérivée classe. Étant donné que MFC fournit un `DllMain` fonction qui est appelée par `_DllMainCRTStartup` pour `DLL_PROCESS_ATTACH` et `DLL_PROCESS_DETACH`, vous ne devez pas écrire votre propre `DllMain` (fonction). Fournie par le MFC `DllMain` les appels de fonction `InitInstance` lorsque votre DLL est chargée et appelle `ExitInstance` avant que la DLL est déchargée.  
  
Une DLL MFC normale peut assurer le suivi de plusieurs threads en appelant [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) et [TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812) dans son `InitInstance` (fonction). Ces fonctions permettent à la DLL effectuer le suivi des données propres au thread.  
  
Dans la DLL MFC normale liée de manière dynamique aux MFC, si vous utilisez OLE MFC, base de données MFC (ou DAO) ou Sockets MFC prend en charge, respectivement, le débogage MFCO de DLL d’extension MFC*version*D.dll, MFCD*version*D.dll et MFCN*version*D.dll (où *version* est le numéro de version) sont automatiquement liées. Vous devez appeler l’une des fonctions d’initialisation prédéfinies suivantes pour chacune de ces DLL que vous utilisez dans votre MFC DLL régulière `CWinApp::InitInstance`.  
  
|Type de prise en charge MFC|Fonction d’initialisation à appeler|  
|-------------------------|-------------------------------------|  
|OLE MFC (MFCO*version*D.dll)|`AfxOleInitModule`|  
|Base de données MFC (MFCD*version*D.dll)|`AfxDbInitModule`|  
|Sockets MFC (MFCN*version*D.dll)|`AfxNetInitModule`|  
  
<a name="initializing-extension-dlls"></a>  
  
### <a name="initialize-mfc-extension-dlls"></a>Initialiser les DLL d’extension MFC  
  
DLL d’extension MFC n’ont pas un `CWinApp`-dérivée de l’objet (comme les DLL régulières MFC), vous devez ajouter votre code d’initialisation et d’arrêt à la `DllMain` fonction qui génère de l’Assistant DLL MFC.  
  
 L’Assistant fournit le code suivant pour les DLL d’extension MFC. Dans le code, `PROJNAME` est un espace réservé pour le nom de votre projet.  
  
```cpp  
#include "stdafx.h"  
#include <afxdllx.h>  
  
#ifdef _DEBUG  
#define new DEBUG_NEW  
#undef THIS_FILE  
static char THIS_FILE[] = __FILE__;  
#endif  
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };  
  
extern "C" int APIENTRY  
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)  
{  
   if (dwReason == DLL_PROCESS_ATTACH)  
   {  
      TRACE0("PROJNAME.DLL Initializing!\n");  
  
      // MFC extension DLL one-time initialization  
      AfxInitExtensionModule(PROJNAMEDLL,   
                                 hInstance);  
  
      // Insert this DLL into the resource chain  
      new CDynLinkLibrary(Dll3DLL);  
   }  
   else if (dwReason == DLL_PROCESS_DETACH)  
   {  
      TRACE0("PROJNAME.DLL Terminating!\n");  
   }  
   return 1;   // ok  
}  
```  
  
Création d’un `CDynLinkLibrary` objet pendant l’initialisation permet des exporter de la DLL d’extension MFC `CRuntimeClass` objets ou des ressources à l’application cliente.  
  
Si vous vous apprêtez à utiliser la DLL à partir d’une ou plusieurs DLL MFC standard d’extension MFC, vous devez exporter une fonction d’initialisation qui crée un `CDynLinkLibrary` objet. Cette fonction doit être appelée à partir de chacun des DLL régulière MFC qui utilisent la DLL d’extension MFC. Est un emplacement approprié pour appeler cette fonction d’initialisation du `InitInstance` fonction membre de la MFC DLL régulière `CWinApp`-objet dérivé avant d’utiliser une des fonctions ou classes exportées de la DLL d’extension MFC.  
  
Dans le `DllMain` génère que l’Assistant DLL MFC, l’appel à `AfxInitExtensionModule` capture les classes d’exécution du module (`CRuntimeClass` structures), ainsi que ses fabriques d’objets (`COleObjectFactory` objets) pour les utiliser lorsque le `CDynLinkLibrary` objet est créé. Vous devez vérifier la valeur de retour de `AfxInitExtensionModule`; si une valeur zéro est retournée à partir de `AfxInitExtensionModule`, retourner zéro à partir de votre `DllMain` (fonction).  
  
Si votre DLL d’extension MFC doit être explicitement lié à un fichier exécutable (ce qui signifie que l’exécutable appelle `AfxLoadLibrary` à lier à la DLL), vous devez ajouter un appel à `AfxTermExtensionModule` sur `DLL_PROCESS_DETACH`. Cette fonction permet de MFC nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL d’extension MFC (ce qui se produit lorsque le processus s’arrête ou lorsque la DLL est déchargée à la suite d’un `AfxFreeLibrary` appeler). Si votre DLL d’extension MFC sera lié implicitement à l’application, l’appel à `AfxTermExtensionModule` n’est pas nécessaire.  
  
Applications lien vers la DLL d’extension MFC doit appeler explicitement `AfxTermExtensionModule` lors de la libération de la DLL. Ils doivent également utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions Win32 `LoadLibrary` et `FreeLibrary`) si l’application utilise plusieurs threads. À l’aide de `AfxLoadLibrary` et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la DLL est chargé et déchargé d’extension MFC n’altère pas l’état global des MFC.  
  
Étant donné que MFCx0.dll est complètement initialisée au moment `DllMain` est appelée, vous pouvez allouer de la mémoire et appeler des fonctions MFC dans `DllMain` (contrairement à la version 16 bits de MFC).  
  
DLL d’extension peuvent prendre en charge le multithreading en gérant les `DLL_THREAD_ATTACH` et `DLL_THREAD_DETACH` cas dans le `DllMain` (fonction). Ces cas sont passés à `DllMain` lorsque les threads attacher et détacher de la DLL. Appel de [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) lorsque attachement d’une DLL permet à la DLL maintenir le thread de stockage local (TLS) d’index pour chaque thread attaché à la DLL.  
  
Notez que le fichier d’en-tête Afxdllx.h contienne des définitions spéciales pour les structures utilisées dans les DLL d’extension MFC, telles que la définition de `AFX_EXTENSION_MODULE` et `CDynLinkLibrary`. Vous devez inclure ce fichier d’en-tête dans la DLL d’extension MFC.  
  
> [!NOTE]
>  Il est important de ne pas définir ni supprimer de la `_AFX_NO_XXX` macros dans Stdafx.h. Ces macros existent uniquement à des fins de vérification si une plateforme cible particulière prend en charge cette fonctionnalité ou non. Vous pouvez écrire votre programme pour vérifier ces macros (par exemple, `#ifndef _AFX_NO_OLE_SUPPORT`), mais votre programme ne doit jamais définir ou annuler la définition de ces macros.  
  
Un exemple de fonction d’initialisation qui gère le multithreading est inclus dans [à l’aide du stockage Local des threads dans une bibliothèque de liens dynamiques](http://msdn.microsoft.com/library/windows/desktop/ms686997) dans le Kit de développement logiciel Windows. Notez que l’exemple contient une fonction de point d’entrée appelée `LibMain`, mais vous devez nommer cette fonction `DllMain` afin qu’il fonctionne avec les bibliothèques Runtime C et MFC.  
  
## <a name="see-also"></a>Voir aussi  
  
[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)  
[Point d’entrée DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583.aspx)  
[Meilleures pratiques de la bibliothèque de liens dynamiques](https://msdn.microsoft.com/library/windows/desktop/dn633971.aspx)  