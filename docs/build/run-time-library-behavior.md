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

Lorsque vous créez une bibliothèque à liaison dynamique (DLL) en utilisant Visual Studio, par défaut, le lien inclut la bibliothèque Visual CMD run-time (VCRuntime). Le VCRuntime contient le code nécessaire pour initialiser et mettre fin à un C/CMd exécutable. Lorsqu’il est relié à un DLL, le code VCRuntime fournit une fonction interne de point d’entrée DLL appelée `_DllMainCRTStartup` qui gère les messages d’OS Windows au DLL pour s’attacher à un processus ou un thread ou se détacher d’un processus ou d’un thread. La `_DllMainCRTStartup` fonction effectue des tâches essentielles telles que la sécurité tampon de pile mis en place, L’initialisation et la terminaison de bibliothèque de temps d’exécution de C (CRT), et des appels aux constructeurs et aux destructeurs pour des objets statiques et globaux. `_DllMainCRTStartup`appelle également les fonctions de crochet pour d’autres bibliothèques telles que WinRT, MFC, et ATL pour effectuer leur propre initialisation et la résiliation. Sans cette initialisation, la CRT et d’autres bibliothèques, ainsi que vos variables statiques, seraient laissées dans un état uninitialisé. Les mêmes routines d’initialisation interne et de terminaison VCRuntime sont appelées si votre DLL utilise un CRT statiquement lié ou un DLL CRT dynamiquement lié.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Point d’entrée DLL par défaut _DllMainCRTStartup

Dans Windows, tous les DLL peuvent contenir une `DllMain`fonction optionnelle de point d’entrée, généralement appelée , qui est appelé à la fois pour l’initialisation et la résiliation. Cela vous donne l’occasion d’allouer ou de libérer des ressources supplémentaires au besoin. Windows appelle la fonction de point d’entrée dans quatre situations : attacher, traiter le détachement, attacher le fil et détacher le fil. Lorsqu’un DLL est chargé dans un espace d’adresse de processus, soit lorsqu’une application qui l’utilise est chargée, soit lorsque l’application demande le DLL au moment de l’exécution, le système d’exploitation crée une copie distincte des données DLL. C’est ce qu’on appelle *le processus attacher*. *L’attachement de fil* se produit lorsque le processus que le DLL est chargé crée un nouveau thread. *Le détachement de fil* se produit lorsque le thread se termine, et le *processus se détache* lorsque le DLL n’est plus nécessaire et est libéré par une application. Le système d’exploitation fait un appel séparé au point d’entrée DLL pour chacun de ces événements, en passant un argument *de raison* pour chaque type d’événement. Par exemple, le `DLL_PROCESS_ATTACH` système d’exploitation envoie comme *argument de raison* pour signaler le traitement joindre.

La bibliothèque VCRuntime offre une `_DllMainCRTStartup` fonction de point d’entrée appelée pour gérer les opérations d’initialisation et de résiliation par défaut. Sur le traitement `_DllMainCRTStartup` joint, la fonction met en place des contrôles de sécurité tampon, initialise le CRT et d’autres bibliothèques, initialise les informations de type temps d’exécution, initialise et appelle les constructeurs `DllMain`de données statiques et non locales, initialise le stockage thread-local, incréments un compteur statique interne pour chaque attache, puis appelle un utilisateur ou une bibliothèque fournie . Sur le processus de se détacher, la fonction passe par ces étapes à l’envers. Il `DllMain`appelle , décrédit le compteur interne, appelle destructeurs, `atexit` appelle fonctions de terminaison CRT et fonctions enregistrées, et informe toutes les autres bibliothèques de résiliation. Lorsque le compteur de pièce jointe `FALSE` passe à zéro, la fonction revient pour indiquer à Windows que le DLL peut être déchargé. La `_DllMainCRTStartup` fonction est également appelée pendant l’attachement de fil et le fil se détacher. Dans ces cas, le code VCRuntime ne fait pas d’initialisation ou de résiliation supplémentaire à lui seul, et il suffit d’appels `DllMain` pour transmettre le message. Si `DllMain` `FALSE` les retours du processus `_DllMainCRTStartup` `DllMain` se fixent, signalent une défaillance, les appels à nouveau et passe `DLL_PROCESS_DETACH` comme argument de *raison,* puis passe par le reste du processus de résiliation.

Lors de la construction de DLL `_DllMainCRTStartup` dans Visual Studio, le point d’entrée par défaut fourni par VCRuntime est automatiquement lié. Vous n’avez pas besoin de spécifier une fonction de point d’entrée pour votre DLL en utilisant l’option de liaison [/ENTRY (symbole de point d’entrée).](reference/entry-entry-point-symbol.md)

> [!NOTE]
> Bien qu’il soit possible de spécifier une autre fonction de point d’entrée pour un DLL en utilisant l’option /ENTRY: linker, nous ne le recommandons pas, parce que votre fonction de point d’entrée devrait dupliquer tout ce qui `_DllMainCRTStartup` le fait, dans le même ordre. Le VCRuntime fournit des fonctions qui vous permettent de dupliquer son comportement. Par exemple, vous pouvez appeler [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) immédiatement sur le processus joindre pour prendre en charge l’option de vérification tampon [/GS (contrôle de sécurité tampon tampon).](reference/gs-buffer-security-check.md) Vous pouvez `_CRT_INIT` appeler la fonction, en passant les mêmes paramètres que la fonction de point d’entrée, pour effectuer le reste des fonctions d’initialisation ou de terminaison DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Initialiser un DLL

Votre DLL peut avoir le code d’initialisation qui doit s’exécuter lorsque votre DLL se charge. Afin que vous puissiez effectuer vos propres fonctions `_DllMainCRTStartup` d’initialisation `DllMain` et de terminaison DLL, appelle une fonction appelée que vous pouvez fournir. Votre `DllMain` doit avoir la signature requise pour un point d’entrée DLL. La fonction `_DllMainCRTStartup` de `DllMain` point d’entrée par défaut appelle en utilisant les mêmes paramètres passés par Windows. Par défaut, si vous `DllMain` ne fournissez pas une fonction, Visual `_DllMainCRTStartup` Studio vous en fournit une et la relie pour qu’elle ait toujours quelque chose à appeler. Cela signifie que si vous n’avez pas besoin d’initialiser votre DLL, il n’y a rien de spécial que vous avez à faire lors de la construction de votre DLL.

C’est la `DllMain`signature utilisée pour :

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Certaines bibliothèques `DllMain` enveloppent la fonction pour vous. Par exemple, dans un DLL MFC régulier, implémentez les fonctions de l’objet `CWinApp` et `InitInstance` `ExitInstance` du membre pour effectuer l’initialisation et la résiliation requises par votre DLL. Pour plus de détails, consultez la section [MFC DLLs régulière de Initialize.](#initializing-regular-dlls)

> [!WARNING]
> Il ya des limites importantes sur ce que vous pouvez faire en toute sécurité dans un point d’entrée DLL. Voir [les meilleures pratiques générales](/windows/win32/Dlls/dynamic-link-library-best-practices) pour des API Windows spécifiques qui ne sont pas sûrs d’appeler . `DllMain` Si vous avez besoin de quoi que ce soit d’autre que l’initialisation la plus simple, alors faites-le dans une fonction d’initialisation pour le DLL. Vous pouvez exiger des applications pour `DllMain` appeler la fonction d’initialisation après s’est exécuté et avant qu’ils appellent toutes les autres fonctions dans le DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Initialiser les DLL ordinaires (non-MFC)

Pour effectuer votre propre initialisation dans les DLL ordinaires (non-MFC) qui utilisent le point d’entrée fourni par `_DllMainCRTStartup` VCRuntime, votre code source DLL doit contenir une fonction appelée `DllMain`. Le code suivant présente un squelette `DllMain` de base montrant à quoi pourrait ressembler la définition :

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
> La documentation Windows SDK ancienne indique que le nom réel de la fonction DLL point d’entrée doit être spécifié sur la ligne de commande de liaison avec l’option /ENTRY. Avec Visual Studio, vous n’avez pas besoin d’utiliser l’option `DllMain`/ENTRY si le nom de votre fonction de point d’entrée est . En fait, si vous utilisez l’option /ENTRY et `DllMain`nommez votre fonction d’entrée-point autre chose que , le CRT ne se paralyse pas correctement à moins que votre fonction de point d’entrée ne fasse les mêmes appels d’initialisation qui `_DllMainCRTStartup` fait.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Initialiser les DPL MFC réguliers

Étant donné que les DLL MFC ordinaires ont `CWinApp` un objet, ils doivent effectuer leurs `InitInstance` tâches `ExitInstance` d’initialisation et de `CWinApp`terminaison au même endroit qu’une application MFC : dans les fonctions et les membres de la classe dérivée du DLL. Parce que MFC fournit `DllMain` une `_DllMainCRTStartup` `DLL_PROCESS_ATTACH` fonction `DLL_PROCESS_DETACH`qui est appelée `DllMain` par et , vous ne devriez pas écrire votre propre fonction. La fonction fournie `DllMain` par `InitInstance` MFC appelle lorsque votre `ExitInstance` DLL est chargé et il appelle avant que le DLL ne soit déchargé.

Un DLL MFC régulier peut garder une trace de plusieurs threads en `InitInstance` appelant [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) et [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) dans sa fonction. Ces fonctions permettent au DLL de suivre les données spécifiques au thread.

Dans votre MFC DLL régulier qui relie dynamiquement à MFC, si vous utilisez n’importe quel MFC OLE, MFC Database (ou DAO), ou MFC Sockets prendre en charge, respectivement, l’extension de débbug MFC DLLs*MFCO version*D.dll, MFCD*version*D.dll, et MFCN*version*D.dll (où la *version* est le numéro de version) sont liés automatiquement. Vous devez appeler l’une des fonctions d’initialisation prédéfinie suivantes pour chacun de ces `CWinApp::InitInstance`DLL que vous utilisez dans votre MFC DLL régulière .

|Type de support MFC|Fonction de initialisation à appeler|
|-------------------------|-------------------------------------|
|MFC OLE *(version*MFCO D.dll)|`AfxOleInitModule`|
|MFC Database *(version*MFCD D.dll)|`AfxDbInitModule`|
|MFC Sockets *(version*MFCN D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Initialiser les DLL d’extension MFC

Étant donné que les DLL `CWinApp`d’extension MFC n’ont pas d’objet dérivé (comme le `DllMain` font les DLL MFC réguliers), vous devez ajouter votre code d’initialisation et de terminaison à la fonction générée par le MFC DLL Wizard.

L’assistant fournit le code suivant pour les DLL d’extension MFC. Dans le `PROJNAME` code, est un espace réservé pour le nom de votre projet.

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

La création `CDynLinkLibrary` d’un nouvel objet lors de `CRuntimeClass` l’initialisation permet au DLL d’extension MFC d’exporter des objets ou des ressources vers l’application client.

Si vous allez utiliser votre DLL d’extension MFC à partir d’un ou plusieurs DLFC réguliers, vous devez exporter une fonction d’initialisation qui crée un `CDynLinkLibrary` objet. Cette fonction doit être appelée à partir de chacun des DLL MFC réguliers qui utilisent l’extension MFC DLL. Un endroit approprié pour appeler cette `InitInstance` fonction d’initialisation est dans `CWinApp`la fonction membre de l’objet MFC DLL-dérivé régulier avant d’utiliser l’une des classes ou fonctions exportées de l’extension de la MFC DLL.

Dans `DllMain` le produit généré par le MFC `AfxInitExtensionModule` DLL Wizard, l’appel pour`CRuntimeClass` capturer les classes de`COleObjectFactory` temps d’exécution `CDynLinkLibrary` du module (structures) ainsi que ses usines d’objets (objets) pour une utilisation lorsque l’objet est créé. Vous devez vérifier la `AfxInitExtensionModule`valeur de retour de ; si une valeur zéro `AfxInitExtensionModule`est retournée `DllMain` de , retour zéro de votre fonction.

Si votre extension MFC DLL sera explicitement liée à un `AfxLoadLibrary` exécutant (ce qui signifie que les `AfxTermExtensionModule` `DLL_PROCESS_DETACH`appels exécutables à lier à la DLL), vous devez ajouter un appel à . Cette fonction permet à MFC de nettoyer la DLL d’extension MFC lorsque chaque processus se détache de l’extension MFC DLL `AfxFreeLibrary` (qui se produit lorsque le processus sort ou lorsque le DLL est déchargé à la suite d’un appel). Si votre DLL d’extension MFC sera implicitement `AfxTermExtensionModule` lié à l’application, l’appel à n’est pas nécessaire.

Les applications qui se lient explicitement `AfxTermExtensionModule` à LPL d’extension MFC doivent appeler lors de la libération de la DLL. Ils doivent `AfxLoadLibrary` également `AfxFreeLibrary` utiliser et (au lieu `LoadLibrary` `FreeLibrary`des fonctions Win32 et ) si l’application utilise plusieurs threads. L’utilisation `AfxLoadLibrary` et `AfxFreeLibrary` la sécurité que le code de démarrage et d’arrêt qui s’exécute lorsque l’extension MFC DLL est chargé et déchargé ne corrompt pas l’état mondial MFC.

Parce que le MFCx0.dll est `DllMain` entièrement paraséminé par le temps est `DllMain` appelé, vous pouvez allouer la mémoire et appeler les fonctions MFC dans (contrairement à la version 16 bits de MFC).

Les DLL d’extension peuvent s’occuper `DLL_THREAD_ATTACH` `DLL_THREAD_DETACH` de la `DllMain` multithreading en traitant les cas et les cas dans la fonction. Ces cas sont `DllMain` transmis au moment où les fils se fixent et se détachent de la DLL. Appeler [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) lorsqu’un DLL est attachant permet au DLL de maintenir les index de stockage local de thread (TLS) pour chaque thread attaché au DLL.

Notez que le fichier d’en-tête Afxdllx.h contient des définitions spéciales `AFX_EXTENSION_MODULE` pour `CDynLinkLibrary`les structures utilisées dans les DLL d’extension MFC, telles que la définition pour et . Vous devez inclure ce fichier d’en-tête dans votre DLL d’extension MFC.

> [!NOTE]
> Il est important que vous ne définissiez ni ne définissez aucune `_AFX_NO_XXX` des macros dans *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt). Ces macros n’existent que dans le but de vérifier si une plate-forme cible particulière prend en charge cette fonctionnalité ou non. Vous pouvez écrire votre programme pour vérifier `#ifndef _AFX_NO_OLE_SUPPORT`ces macros (par exemple, ), mais votre programme ne devrait jamais définir ou indéfinis ces macros.

Une fonction d’initialisation de l’échantillon qui gère la multithreading est incluse dans [l’utilisation du stockage local de thread dans une bibliothèque dynamic-Link](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) dans le SDK Windows. Notez que l’échantillon contient `LibMain`une fonction d’entrée-point appelé , mais vous devez nommer cette fonction `DllMain` de sorte qu’il fonctionne avec les bibliothèques MFC et C run-time.

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)<br/>
[Point d’entrée DllMain](/windows/win32/Dlls/dllmain)<br/>
[Pratiques exemplaires en matière de bibliothèques dynamiques](/windows/win32/Dlls/dynamic-link-library-best-practices)
