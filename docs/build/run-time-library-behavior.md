---
title: DLL et comportement de la bibliothèque runtime Visual C++
ms.date: 08/19/2019
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
ms.openlocfilehash: 2f2ffb13e6a80b144298bbf8cd76b5666a10b4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335666"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLL et comportement de la bibliothèque runtime Visual C++

Lorsque vous générez une bibliothèque de liens dynamiques (DLL) à l’aide de Visual Studio, par défaut, l’éditeur de liens comprend la bibliothèque Runtime Visual C++ (VCRuntime). VCRuntime contient le code requis pour initialiser et terminer un exécutable C/C++. Lorsqu’il est lié à une DLL, le code VCRuntime fournit une fonction de point d’entrée `_DllMainCRTStartup` dll interne appelée qui gère les messages du système d’exploitation Windows dans la dll pour s’attacher ou se détacher d’un processus ou d’un thread. La `_DllMainCRTStartup` fonction effectue des tâches essentielles telles que la configuration de la sécurité de la mémoire tampon de la pile, l’initialisation et l’arrêt de la bibliothèque Runtime C (CRT) et les appels aux constructeurs et aux destructeurs pour les objets statiques et globaux. `_DllMainCRTStartup`appelle également des fonctions de raccordement pour d’autres bibliothèques telles que WinRT, MFC et ATL pour effectuer leur propre initialisation et terminaison. Sans cette initialisation, la bibliothèque CRT et d’autres bibliothèques, ainsi que vos variables statiques, seraient laissées dans un État non initialisé. Les mêmes routines d’initialisation et d’arrêt internes VCRuntime sont appelées si votre DLL utilise un CRT lié de manière statique ou une DLL CRT liée de manière dynamique.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Point d’entrée de la DLL par défaut _DllMainCRTStartup

Dans Windows, toutes les dll peuvent contenir une fonction de point d’entrée facultative, `DllMain`généralement appelée, qui est appelée à la fois pour l’initialisation et l’arrêt. Cela vous donne la possibilité d’allouer ou de libérer des ressources supplémentaires en fonction des besoins. Windows appelle la fonction de point d’entrée dans quatre cas : attachement de processus, détachement de processus, attachement de thread et détachement de thread. Lorsqu’une DLL est chargée dans un espace d’adressage de processus, soit lorsqu’une application qui l’utilise est chargée, soit lorsque l’application demande la DLL au moment de l’exécution, le système d’exploitation crée une copie distincte des données DLL. C’est ce que l’on appelle un *attachement de processus*. L' *attachement de thread* se produit lorsque le processus dans lequel la dll est chargée crée un nouveau thread. Le *détachement de thread* se produit lorsque le thread se termine, et le *détachement de processus* est lorsque la dll n’est plus nécessaire et est libérée par une application. Le système d’exploitation effectue un appel séparé au point d’entrée de la DLL pour chacun de ces événements, en passant un argument *reason* pour chaque type d’événement. Par exemple, le système d' `DLL_PROCESS_ATTACH` exploitation envoie comme argument *reason* pour signaler le processus Attach.

La bibliothèque VCRuntime fournit une fonction de point d’entrée `_DllMainCRTStartup` appelée pour gérer les opérations d’initialisation et d’arrêt par défaut. Sur le processus d’attachement `_DllMainCRTStartup` , la fonction configure les contrôles de sécurité de la mémoire tampon, initialise la bibliothèque CRT et d’autres bibliothèques, initialise les informations de type au moment de l’exécution, initialise et appelle les constructeurs pour les données statiques et non locales, initialise le stockage local des threads, incrémente un compteur statique interne pour chaque `DllMain`attachement, puis appelle un utilisateur ou un bibliothèque. Lors du détachement de processus, la fonction passe en revue ces étapes en sens inverse. Il appelle `DllMain`, décrémente le compteur interne, appelle des destructeurs, appelle des fonctions de terminaison CRT `atexit` et des fonctions inscrites, et notifie toutes les autres bibliothèques de terminaison. Lorsque le compteur de pièce jointe atteint la valeur zéro `FALSE` , la fonction retourne pour indiquer à Windows que la dll peut être déchargée. La `_DllMainCRTStartup` fonction est également appelée pendant l’attachement de thread et le détachement de thread. Dans ce cas, le code VCRuntime n’effectue pas d’initialisation ou d’arrêt supplémentaire, et appelle `DllMain` simplement pour transmettre le message. Si `DllMain` retourne `FALSE` de l’attachement de processus, échec de `_DllMainCRTStartup` signalement, `DllMain` rappelle `DLL_PROCESS_DETACH` et passe en tant qu’argument *reason* , passe au reste du processus d’arrêt.

Lors de la génération de dll dans Visual Studio, le `_DllMainCRTStartup` point d’entrée par défaut fourni par VCRuntime est lié automatiquement. Vous n’avez pas besoin de spécifier une fonction de point d’entrée pour votre DLL à l’aide de l’option de l’éditeur de liens [/entry (symbole de point d’entrée)](reference/entry-entry-point-symbol.md) .

> [!NOTE]
> Bien qu’il soit possible de spécifier une autre fonction de point d’entrée pour une DLL à l’aide de l’option/ENTRY : linker, nous ne la recommandons pas, car la fonction de point d’entrée doit `_DllMainCRTStartup` dupliquer tout ce qui le fait, dans le même ordre. VCRuntime fournit des fonctions qui vous permettent de dupliquer son comportement. Par exemple, vous pouvez appeler [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) immédiatement sur l’attachement de processus pour prendre en charge l’option de vérification de la mémoire tampon [/GS (vérification de la sécurité de la mémoire tampon)](reference/gs-buffer-security-check.md) . Vous pouvez appeler la `_CRT_INIT` fonction, en passant les mêmes paramètres que la fonction de point d’entrée, pour exécuter le reste des fonctions d’initialisation ou d’arrêt de la dll.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Initialiser une DLL

Votre DLL peut comporter un code d’initialisation qui doit s’exécuter lors du chargement de la DLL. Pour que vous puissiez effectuer vos propres fonctions d’initialisation et d’arrêt de la `_DllMainCRTStartup` dll, appelle une `DllMain` fonction appelée que vous pouvez fournir. Votre `DllMain` doit avoir la signature requise pour un point d’entrée de dll. La fonction `_DllMainCRTStartup` de point d’entrée `DllMain` par défaut appelle en utilisant les mêmes paramètres que ceux passés par Windows. Par défaut, si vous ne fournissez pas `DllMain` de fonction, Visual Studio en fournit un pour vous et le lie à `_DllMainCRTStartup` afin qu’il ait toujours un nom à appeler. Cela signifie que si vous n’avez pas besoin d’initialiser votre DLL, vous n’avez rien de spécial à faire lors de la génération de votre DLL.

Il s’agit de la signature `DllMain`utilisée pour :

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Certaines bibliothèques encapsulent la `DllMain` fonction pour vous. Par exemple, dans une DLL MFC standard, implémentez `CWinApp` les fonctions `InitInstance` membres `ExitInstance` et de l’objet pour effectuer l’initialisation et l’arrêt requis par votre dll. Pour plus d’informations, consultez la section [initialiser des DLL MFC normales](#initializing-regular-dlls) .

> [!WARNING]
> Il existe des limites significatives sur ce que vous pouvez faire en toute sécurité dans un point d’entrée de DLL. Consultez les [meilleures pratiques générales](/windows/win32/Dlls/dynamic-link-library-best-practices) pour des API Windows spécifiques qui ne sont pas sûres `DllMain`à appeler dans. Si vous n’avez besoin que de l’initialisation la plus simple, faites-le dans une fonction d’initialisation pour la DLL. Vous pouvez demander aux applications d’appeler la fonction d’initialisation `DllMain` après l’exécution de et avant d’appeler d’autres fonctions dans la dll.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Initialiser des dll ordinaires (non-MFC)

Pour effectuer votre propre initialisation dans des dll ordinaires (non-MFC) qui utilisent le point d’entrée `_DllMainCRTStartup` fourni par VCRuntime, votre code source de dll doit contenir une `DllMain`fonction appelée. Le code suivant présente une structure de `DllMain` base qui montre à quoi doit ressembler la définition :

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
> L’ancienne documentation de SDK Windows indique que le nom réel de la fonction de point d’entrée de la DLL doit être spécifié sur la ligne de commande de l’éditeur de liens avec l’option/ENTRY. Avec Visual Studio, vous n’avez pas besoin d’utiliser l’option/ENTRY si le nom de la fonction de point d' `DllMain`entrée est. En fait, si vous utilisez l’option/ENTRY et que vous nommez la fonction de point d' `DllMain`entrée autre que, le CRT n’est pas correctement initialisé, sauf si votre fonction de point d’entrée effectue les `_DllMainCRTStartup` mêmes appels d’initialisation que ceux effectués par.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Initialiser des DLL MFC normales

Étant donné que les DLL MFC `CWinApp` standard ont un objet, elles doivent effectuer leurs tâches d’initialisation et d’arrêt au même emplacement qu’une application MFC `InitInstance` : `ExitInstance` dans les fonctions membres et de `CWinApp`la classe dérivée de la dll. Étant donné que MFC `DllMain` fournit une fonction qui est `_DllMainCRTStartup` appelée `DLL_PROCESS_ATTACH` par `DLL_PROCESS_DETACH`pour et, vous ne devez pas `DllMain` écrire votre propre fonction. La fonction fournie `DllMain` par MFC appelle `InitInstance` lorsque votre dll est chargée et qu’elle `ExitInstance` appelle avant le déchargement de la dll.

Une DLL MFC normale peut effectuer le suivi de plusieurs threads en appelant [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) et [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) dans sa `InitInstance` fonction. Ces fonctions permettent à la DLL de suivre les données spécifiques aux threads.

Dans votre DLL MFC normale liée de manière dynamique aux MFC, si vous utilisez une bibliothèque OLE MFC, une base de données MFC (ou DAO) ou une prise en charge des sockets MFC, respectivement, les dll d’extension de débogage MFCO*version*d. dll, MFCD*version*d. dll et MFCN*version*d. dll (où *version* est le numéro de version) sont liées automatiquement. Vous devez appeler l’une des fonctions d’initialisation prédéfinies suivantes pour chacune des dll que vous utilisez dans vos DLL MFC normales `CWinApp::InitInstance`.

|Type de prise en charge MFC|Fonction d’initialisation à appeler|
|-------------------------|-------------------------------------|
|OLE MFC (MFCO*version*D. dll)|`AfxOleInitModule`|
|Base de données MFC (*version*MFCD D. dll)|`AfxDbInitModule`|
|Sockets MFC (*version*MFCN D. dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Initialiser les dll d’extension MFC

Étant donné que les dll d’extension MFC `CWinApp`n’ont pas d’objet dérivé de (comme les DLL MFC normales), vous devez ajouter votre code d’initialisation `DllMain` et d’arrêt à la fonction générée par l’Assistant DLL MFC.

L’Assistant fournit le code suivant pour les dll d’extension MFC. Dans le code, `PROJNAME` est un espace réservé pour le nom de votre projet.

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
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

La création d' `CDynLinkLibrary` un objet pendant l’initialisation permet à la dll d’extension `CRuntimeClass` MFC d’exporter des objets ou des ressources vers l’application cliente.

Si vous prévoyez d’utiliser votre DLL d’extension MFC à partir d’une ou de plusieurs DLL MFC standard, vous devez exporter une fonction d’initialisation `CDynLinkLibrary` qui crée un objet. Cette fonction doit être appelée à partir de chacune des DLL MFC classiques qui utilisent la DLL d’extension MFC. L’emplacement approprié pour appeler cette fonction d’initialisation se trouve dans `InitInstance` la fonction membre de l’objet dérivé de `CWinApp`la DLL MFC normale avant d’utiliser l’une des classes ou fonctions exportées de la dll d’extension MFC.

Dans le `DllMain` que l’Assistant DLL MFC génère, l’appel à `AfxInitExtensionModule` capture les classes d’exécution du module (`CRuntimeClass` structures) ainsi que ses fabriques d’objets (`COleObjectFactory` objets) à utiliser lors de la `CDynLinkLibrary` création de l’objet. Vous devez vérifier la valeur de retour `AfxInitExtensionModule`de ; Si une valeur zéro est retournée `AfxInitExtensionModule`à partir de, retournez `DllMain` zéro à partir de votre fonction.

Si votre DLL d’extension MFC est explicitement liée à un fichier exécutable (ce qui signifie que les `AfxLoadLibrary` appels exécutables sont liés à la dll), vous devez ajouter `AfxTermExtensionModule` un `DLL_PROCESS_DETACH`appel à on. Cette fonction permet à MFC de nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL d’extension MFC (ce qui se produit lorsque le processus se termine ou lorsque la DLL est déchargée `AfxFreeLibrary` à la suite d’un appel). Si votre DLL d’extension MFC est liée de manière implicite à l’application, l' `AfxTermExtensionModule` appel à n’est pas nécessaire.

Les applications qui sont liées explicitement aux DLL d’extension `AfxTermExtensionModule` MFC doivent appeler lors de la libération de la dll. Ils doivent également utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions `LoadLibrary` Win32 et `FreeLibrary`) si l’application utilise plusieurs threads. L' `AfxLoadLibrary` utilisation `AfxFreeLibrary` de et garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la dll d’extension MFC est chargée et déchargée n’endommage pas l’état global des MFC.

Étant donné que MFCx0. dll est entièrement initialisé par l’heure `DllMain` , vous pouvez allouer de la mémoire et appeler des fonctions `DllMain` MFC dans (contrairement à la version 16 bits de MFC).

Les dll d’extension peuvent prendre en charge le multithreading `DLL_THREAD_ATTACH` en `DLL_THREAD_DETACH` gérant les cas `DllMain` et dans la fonction. Ces cas sont passés à `DllMain` lorsque les threads s’attachent et se détachent de la dll. L’appel de [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) quand une dll est attachée permet à la dll de conserver les index de stockage local des threads (TLS) pour chaque thread attaché à la dll.

Notez que le fichier d’en-tête Afxdllx. h contient des définitions spéciales pour les structures utilisées dans les dll d’extension `AFX_EXTENSION_MODULE` MFC `CDynLinkLibrary`, telles que la définition pour et. Vous devez inclure ce fichier d’en-tête dans votre DLL d’extension MFC.

> [!NOTE]
> Il est important de ne pas définir ni d’annuler la `_AFX_NO_XXX` définition des macros dans *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures). Ces macros existent uniquement dans le but de vérifier si une plateforme cible particulière prend en charge cette fonctionnalité ou non. Vous pouvez écrire votre programme pour vérifier ces macros (par exemple, `#ifndef _AFX_NO_OLE_SUPPORT`), mais votre programme ne doit jamais définir ou annuler la définition de ces macros.

Un exemple de fonction d’initialisation qui gère le multithreading est inclus dans [l’utilisation du stockage local des threads dans une bibliothèque de liens dynamiques](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) dans le SDK Windows. Notez que l’exemple contient une fonction de point d’entrée `LibMain`appelée, mais vous devez nommer cette `DllMain` fonction pour qu’elle fonctionne avec les bibliothèques Runtime C et MFC.

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)<br/>
[Point d’entrée DllMain](/windows/win32/Dlls/dllmain)<br/>
[Meilleures pratiques pour la bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-best-practices)
