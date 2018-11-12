---
title: DLL et comportement de la bibliothèque d’exécution Visual C++
ms.date: 11/04/2016
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
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
ms.openlocfilehash: 8293e2e05193b34802aba0af722dd06155fdcd81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429053"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLL et comportement de la bibliothèque d’exécution Visual C++

Lorsque vous générez une bibliothèque de liens dynamiques (DLL) à l’aide de Visual C++, par défaut, l’éditeur de liens inclut la bibliothèque d’exécution Visual C++ (VCRuntime). Le VCRuntime contient le code nécessaire à l’initialisation et de fin d’un fichier exécutable C/C++. Quand liées dans une DLL, le code VCRuntime fournit une fonction de point d’entrée DLL interne appelée `_DllMainCRTStartup` qui gère les messages de système d’exploitation Windows à la DLL pour attacher ou détacher un processus ou thread. Le `_DllMainCRTStartup` fonction effectue des tâches essentielles telles que la sécurité de mémoire tampon de pile configuré, l’initialisation de C Runtime library (CRT) et l’arrêt et appelle aux constructeurs et destructeurs des objets statiques et globales. `_DllMainCRTStartup` également appelle les fonctions pour d’autres bibliothèques telles que WinRT, MFC et ATL pour effectuer leurs propres l’initialisation et l’arrêt de raccordement. Sans cette initialisation, la bibliothèque CRT et autres bibliothèques, ainsi que des variables statiques, serait un état non initialisé. Si votre DLL utilise un CRT lié de manière statique ou une DLL CRT lié dynamiquement de la même initialisation interne VCRuntime et les routines d’arrêt sont appelées.

## <a name="default-dll-entry-point-dllmaincrtstartup"></a>Par défaut _DllMainCRTStartup de point d’entrée DLL

Dans Windows, toutes les DLL peuvent contenir une fonction de point d’entrée facultatif, généralement appelée `DllMain`, qui est appelée pour l’initialisation et arrêt. Cela vous donne la possibilité d’allouer ou de libérer des ressources supplémentaires en fonction des besoins. Windows appelle la fonction de point d’entrée dans quatre situations : attachement de processus, détacher un processus, attachement de thread et détachement de thread. Lorsqu’une DLL est chargée dans un espace d’adressage de processus, lorsqu’une application qui l’utilise est chargée, ou lorsque l’application demande la DLL lors de l’exécution, le système d’exploitation crée une copie distincte des données DLL. Il s’agit *attacher un processus*. *Attachement de thread* se produit lorsque le processus de chargement de la DLL en crée un nouveau thread. *Détachement de thread* se produit lorsque le thread s’arrête, et *détacher un processus* est lorsque la DLL n’est plus nécessaire et est publiée par une application. Le système d’exploitation effectue un appel distinct pour le point d’entrée DLL pour chacun de ces événements, en passant un *raison* argument pour chaque type d’événement. Par exemple, le système d’exploitation envoie `DLL_PROCESS_ATTACH` en tant que le *raison* argument pour signaler des processus d’attachement.

La bibliothèque VCRuntime fournit une fonction de point d’entrée appelée `_DllMainCRTStartup` pour gérer les opérations d’initialisation et d’arrêt par défaut. Sur le processus d’attachement, le `_DllMainCRTStartup` fonction configure les vérifications de sécurité de mémoire tampon, initialise la bibliothèque CRT et autres bibliothèques, initialise les informations de type au moment de l’exécution, initialise et appelle les constructeurs pour les données statiques et non local, initialise le stockage local des threads , incrémente un compteur interne statique pour chaque attacher et appelle ensuite une ou bibliothèque-fournie par l’utilisateur `DllMain`. Sur le processus de détachement, la fonction effectue les étapes dans l’ordre inverse. Il appelle `DllMain`décrémente le compteur interne, appelle des destructeurs, arrêt des appels CRT, fonctions et inscrit `atexit` functions et indique à d’autres bibliothèques d’arrêt. Lorsque le compteur de pièce jointe tend vers zéro, la fonction retourne `FALSE` pour indiquer à Windows que la DLL peut être déchargée. Le `_DllMainCRTStartup` fonction est également appelée pendant thread attachement et détachement de thread. Dans ce cas, le code VCRuntime n’aucune initialisation supplémentaire ou l’arrêt de sa propre et appelle simplement `DllMain` pour transmettre le message. Si `DllMain` retourne `FALSE` à partir de processus attacher, échec, de signalisation `_DllMainCRTStartup` appels `DllMain` à nouveau et passe `DLL_PROCESS_DETACH` en tant que le *raison* argument, puis passe par le reste de la processus d’arrêt.

Lors de la création de DLL dans Visual C++, le point d’entrée par défaut `_DllMainCRTStartup` fourni par VCRuntime est liée automatiquement. Vous n’avez pas besoin de spécifier une fonction de point d’entrée pour votre DLL en utilisant la [/ENTRY (symbole de point d’entrée)](../build/reference/entry-entry-point-symbol.md) option de l’éditeur de liens.

> [!NOTE]
> Bien qu’il soit possible de spécifier une autre fonction de point d’entrée pour une DLL à l’aide de la/Entry : option de l’éditeur de liens, nous ne recommandons pas, car la fonction de point d’entrée aurait à dupliquer tout ce qui `_DllMainCRTStartup` est le cas, dans le même ordre. Le VCRuntime fournit des fonctions qui vous permettent de dupliquer son comportement. Par exemple, vous pouvez appeler [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) immédiatement sur le processus d’attachement pour prendre en charge la [/GS (vérification de sécurité de mémoire tampon)](../build/reference/gs-buffer-security-check.md) mémoire tampon de l’option de vérification. Vous pouvez appeler la `_CRT_INIT` fonction, en passant les mêmes paramètres que la fonction de point d’entrée, pour effectuer le reste des fonctions DLL initialisation ou d’arrêt.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Initialiser une DLL

Votre DLL peut avoir le code d’initialisation qui doit s’exécuter lors de la charge de votre DLL. Dans l’ordre pour effectuer vos propres fonctions d’initialisation et suppression de DLL, `_DllMainCRTStartup` appelle une fonction appelée `DllMain` que vous pouvez fournir. Votre `DllMain` doit avoir la signature requise pour un point d’entrée DLL. La fonction de point d’entrée par défaut `_DllMainCRTStartup` appels `DllMain` utilisant les mêmes paramètres passés par Windows. Par défaut, si vous ne fournissez pas un `DllMain` (fonction), Visual C++ fournit un pour vous et le lie dans afin que `_DllMainCRTStartup` a toujours quelque chose à appeler. Cela signifie que si vous n’avez pas besoin d’initialiser la DLL, il n’est rien de spécial à que faire lors de la création de votre DLL.

Voici la signature utilisée pour `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Certaines bibliothèques encapsulent le `DllMain` (fonction) pour vous. Par exemple, dans une DLL MFC normale, mettre en œuvre la `CWinApp` l’objet `InitInstance` et `ExitInstance` des fonctions membres pour effectuer l’initialisation et arrêt requises par votre DLL. Pour plus d’informations, consultez le [initialiser regular DLL MFC](#initializing-regular-dlls) section.

> [!WARNING]
> Il existe des limites significatives sur ce que vous pouvez faire en toute sécurité dans un point d’entrée DLL. Consultez [meilleures pratiques générales](/windows/desktop/Dlls/dynamic-link-library-best-practices) des API Windows spécifiques qui sont risqué d’appeler `DllMain`. Si vous avez besoin n’est pas l’initialisation de la plus simple puis faire dans une fonction d’initialisation pour la DLL. Vous pouvez exiger des applications d’appeler la fonction d’initialisation après `DllMain` a exécution et avant qu’ils appellent des autres fonctions dans la DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Initialiser des DLL ordinaires (non-MFC)

Pour effectuer votre propre initialisation dans les DLL ordinaires (non-MFC) qui utilisent le VCRuntime fourni `_DllMainCRTStartup` point d’entrée, votre code source de la DLL doit contenir une fonction appelée `DllMain`. Le code suivant présente une structure de base indiquant quelles la définition de `DllMain` peut ressembler à :

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
> Documentation du SDK Windows plus ancienne indique que le nom réel de la fonction de point d’entrée DLL doit être spécifié sur l’éditeur de liens de la ligne de commande avec l’option/Entry. Avec Visual C++, vous n’avez pas besoin d’utiliser l’option /ENTRY si le nom de votre fonction de point d’entrée est `DllMain`. En fait, si vous utilisez l’option /ENTRY et le nom de votre point d’entrée de fonction quelque chose autres que `DllMain`, la bibliothèque CRT ne pas initialisée correctement, sauf si votre fonction de point d’entrée rend les mêmes appels d’initialisation qui `_DllMainCRTStartup` rend.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Initialiser des DLL MFC normales

Étant donné que les DLL MFC normales ont un `CWinApp` de l’objet, ils doivent effectuer leurs tâches d’initialisation et d’arrêt dans le même emplacement qu’une application MFC : dans le `InitInstance` et `ExitInstance` fonctions membres de la DLL `CWinApp`-dérivée classe. Étant donné que MFC fournit un `DllMain` fonction est appelée par `_DllMainCRTStartup` pour `DLL_PROCESS_ATTACH` et `DLL_PROCESS_DETACH`, vous ne devez pas écrire votre propre `DllMain` (fonction). Fourni par le MFC `DllMain` appels de fonction `InitInstance` lorsque votre DLL est chargée et il appelle `ExitInstance` avant que la DLL est déchargée.

Une DLL MFC normale peut assurer le suivi de plusieurs threads en appelant [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc) et [TlsGetValue](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) dans son `InitInstance` (fonction). Ces fonctions permettent à la DLL effectuer le suivi des données propres au thread.

Dans la DLL MFC normale liée de manière dynamique aux MFC, si vous utilisez OLE MFC, base de données MFC (ou DAO) ou Sockets MFC prend en charge, respectivement, le débogage MFCO de DLL d’extension MFC*version*D.dll, MFCD*version*D.dll et MFCN*version*D.dll (où *version* est le numéro de version) sont automatiquement liées. Vous devez appeler une des fonctions d’initialisation prédéfinies suivantes pour chacune de ces DLL que vous utilisez dans votre MFC DLL régulière `CWinApp::InitInstance`.

|Type de prise en charge MFC|Fonction d’initialisation à appeler|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*version*D.dll)|`AfxOleInitModule`|
|Base de données MFC (MFCD*version*D.dll)|`AfxDbInitModule`|
|Les Sockets de MFC (MFCN*version*D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Initialiser des DLL d’extension MFC

Comme les DLL d’extension MFC n’ont pas un `CWinApp`-dérivée de l’objet (comme les DLL MFC normales), vous devez ajouter votre code d’initialisation et d’arrêt pour le `DllMain` fonction qui génère de l’Assistant DLL MFC.

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

Création d’un nouveau `CDynLinkLibrary` objet pendant l’initialisation permet l’extension MFC DLL pour exporter `CRuntimeClass` objets ou des ressources à l’application cliente.

Si vous vous apprêtez à utiliser la DLL à partir d’un ou plusieurs des DLL MFC normales d’extension MFC, vous devez exporter une fonction d’initialisation qui crée un `CDynLinkLibrary` objet. Cette fonction doit être appelée à partir de chacun des DLL régulière MFC qui utilisent la DLL d’extension MFC. Est un emplacement approprié pour appeler cette fonction d’initialisation du `InitInstance` fonction membre de la MFC DLL régulière `CWinApp`-objet dérivé avant d’utiliser une des fonctions ou classes exportées de la DLL d’extension MFC.

Dans le `DllMain` que l’Assistant DLL MFC génère, l’appel à `AfxInitExtensionModule` capture les classes d’exécution du module (`CRuntimeClass` structures), ainsi que ses fabriques d’objets (`COleObjectFactory` objets) pour utiliser lorsque le `CDynLinkLibrary` objet est créé. Vous devez vérifier la valeur de retour de `AfxInitExtensionModule`; si une valeur zéro est retournée à partir de `AfxInitExtensionModule`, retournent la valeur zéro à partir de votre `DllMain` (fonction).

Si votre DLL d’extension MFC doit être explicitement lié à un fichier exécutable (ce qui signifie que l’exécutable appelle `AfxLoadLibrary` à lier à la DLL), vous devez ajouter un appel à `AfxTermExtensionModule` sur `DLL_PROCESS_DETACH`. Cette fonction permet de MFC nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL d’extension MFC (ce qui se produit lorsque le processus se termine ou lorsque la DLL est déchargée à la suite d’un `AfxFreeLibrary` appeler). Si votre DLL d’extension MFC est liée de manière implicite à l’application, l’appel à `AfxTermExtensionModule` n’est pas nécessaire.

Applications lien vers la DLL d’extension MFC doit appeler explicitement `AfxTermExtensionModule` lors de la libération de la DLL. Ils doivent également utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions Win32 `LoadLibrary` et `FreeLibrary`) si l’application utilise plusieurs threads. À l’aide de `AfxLoadLibrary` et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque l’extension MFC DLL est chargé et déchargé n’altère pas l’état global de MFC.

Étant donné que MFCx0.dll est entièrement initialisé par l’heure `DllMain` est appelée, vous pouvez allouer de la mémoire et appeler des fonctions MFC dans `DllMain` (contrairement à la version 16 bits de MFC).

DLL d’extension peuvent prendre en charge le multithreading en gérant les `DLL_THREAD_ATTACH` et `DLL_THREAD_DETACH` cas dans le `DllMain` (fonction). Ces cas sont passés à `DllMain` lorsque les threads attacher et détacher de la DLL. Appel [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc) lorsque concerne l’attachement d’une DLL permet à la DLL maintenir le thread (TLS) de stockage local des index pour chaque thread attaché à la DLL.

Notez que le fichier d’en-tête Afxdllx.h contienne des définitions spéciales pour les structures utilisées dans les DLL d’extension MFC, telles que la définition de `AFX_EXTENSION_MODULE` et `CDynLinkLibrary`. Vous devez inclure ce fichier d’en-tête dans votre DLL d’extension MFC.

> [!NOTE]
>  Il est important de ne pas définir ni supprimer de la `_AFX_NO_XXX` macros dans Stdafx.h. Ces macros existent uniquement dans le but de vérifier si une plateforme cible particulière prend en charge cette fonctionnalité ou non. Vous pouvez écrire votre programme pour vérifier ces macros (par exemple, `#ifndef _AFX_NO_OLE_SUPPORT`), mais votre programme ne doit jamais définir ou annuler la définition de ces macros.

Un exemple de fonction d’initialisation qui gère le multithreading est inclus dans [à l’aide du stockage Local des threads dans une bibliothèque de liens dynamiques](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library) dans le SDK Windows. Notez que l’exemple contient une fonction de point d’entrée appelée `LibMain`, mais vous devez nommer cette fonction `DllMain` afin qu’il fonctionne avec les bibliothèques Runtime C et MFC.

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)<br/>
[Point d’entrée DllMain](/windows/desktop/Dlls/dllmain)<br/>
[Méthodes conseillées pour la bibliothèque de liens dynamiques](/windows/desktop/Dlls/dynamic-link-library-best-practices)