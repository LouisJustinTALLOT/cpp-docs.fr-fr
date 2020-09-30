---
title: 'Procédure : Utiliser le code C++ existant dans une application de plateforme Windows universelle'
description: Méthodes d’utilisation de vos bibliothèques et applications de code existantes dans les applications plateforme Windows universelle.
ms.date: 09/04/2020
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: fd23c875d67654e96a828f4dba412dd74652912a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503677"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Procédure : Utiliser le code C++ existant dans une application de plateforme Windows universelle

Vous pouvez utiliser du code C++ existant dans des projets plateforme Windows universelle (UWP) de différentes façons. Certaines méthodes ne nécessitent pas que le code soit recompilé avec les extensions de composant (C++/CX) activées (autrement dit, avec l' `/ZW` option), et d’autres. Vous devrez peut-être conserver le code en C++ standard ou conserver un environnement de compilation Win32 classique pour du code. Vous pouvez toujours le faire, avec les choix d’architecture appropriés. Examinez tout votre code contenant l’interface utilisateur UWP et les types exposés aux appelants C#, Visual Basic et JavaScript. Ce code doit se trouver dans les projets d’application Windows et les projets de composant Windows Runtime. Le code que vous appelez uniquement à partir de C++ (y compris C++/CX) peut se trouver dans un projet qui est compilé avec l' `/ZW` option ou un projet C++ standard. Le code binaire uniquement qui n’utilise pas d’API non autorisées peut être utilisé en le liant en tant que bibliothèque statique. Vous pouvez aussi l’empaqueter avec l’application en tant que contenu et la charger dans une DLL.

Le moyen le plus simple d’exécuter votre programme de bureau dans l’environnement UWP consiste peut-être à utiliser les technologies de pont de bureau. Elles incluent le convertisseur d’applications de bureau, qui empaquette votre application existante en tant qu’application UWP sans aucune modification de code. Pour plus d’informations, consultez [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

Le reste de cet article explique comment déplacer des bibliothèques C++ (dll et bibliothèques statiques) vers le plateforme Windows universelle. Vous souhaiterez peut-être déplacer votre code afin que votre logique C++ de base puisse être utilisée avec plusieurs applications UWP.

Les applications UWP s’exécutent dans un environnement protégé. Par conséquent, de nombreux appels d’API Win32, COM et CRT qui peuvent compromettre la sécurité de la plateforme ne sont pas autorisés. L' `/ZW` option du compilateur peut détecter de tels appels et générer une erreur. Vous pouvez utiliser le kit de certification des applications sur votre application pour détecter le code qui appelle des API non autorisées. Pour plus d’informations, consultez [Kit de certification des applications Windows](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Si le code source est disponible pour la bibliothèque, vous pouvez essayer d’éliminer les appels d’API non autorisés. Pour obtenir la liste des API qui ne sont pas autorisées, consultez [API Win32 et com pour les applications UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps) et les [fonctions CRT non prises en charge dans les applications plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Des alternatives sont disponibles dans [Alternatives aux API Windows dans les applications UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Si vous essayez simplement d’ajouter une référence d’un projet Windows universel à une bibliothèque de bureau classique, vous recevez un message d’erreur indiquant que la bibliothèque n’est pas compatible. S’il s’agit d’une bibliothèque statique, vous pouvez établir un lien vers votre bibliothèque en ajoutant la bibliothèque ( *`.lib`* fichier) à votre entrée d’éditeur de liens, de la même façon que vous le feriez dans une application Win32 classique. Si seule une bibliothèque binaire est disponible, il s’agit de la seule option. Une bibliothèque statique est liée à l’exécutable de votre application. Toutefois, une DLL Win32 que vous consommez dans une application UWP doit être empaquetée dans l’application en l’incluant dans le projet et en la marquant comme contenu. Pour charger une DLL Win32 dans une application UWP, vous devez également appeler [`LoadPackagedLibrary`](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) au lieu de `LoadLibrary` ou `LoadLibraryEx` .

Si vous disposez d’un code source pour la DLL ou la bibliothèque statique, vous pouvez le recompiler en tant que projet UWP à l’aide de l' `/ZW` option du compilateur. Vous pouvez ensuite y ajouter une référence à l’aide de la **Explorateur de solutions**et l’utiliser dans les applications UWP C++. Liez la DLL à l’aide de la bibliothèque d’exportation.

Pour exposer des fonctionnalités aux appelants dans d'autres langages, vous pouvez convertir la bibliothèque en composant Windows Runtime. Windows Runtime composants diffèrent des dll ordinaires en ce sens qu’ils incluent des métadonnées sous la forme de *`.winmd`* fichiers qui décrivent le contenu d’une manière que les consommateurs .net et JavaScript requièrent.  Pour exposer des éléments d’API à d’autres langages, vous pouvez ajouter des constructions C++/CX, telles que des classes REF, et les rendre publiques. Dans Windows 10 et versions ultérieures, nous recommandons la [bibliothèque c++/WinRT](https://github.com/microsoft/cppwinrt) au lieu de c++/CX.

La discussion précédente ne s’applique pas aux composants COM, qui doivent être gérés différemment. Si vous avez un serveur COM dans un fichier EXE ou DLL, vous pouvez l’utiliser dans un projet Windows universel. Empaquetez-le en tant que [composant COM sans inscription](/windows/win32/sbscs/creating-registration-free-com-objects), ajoutez-le à votre projet en tant que fichier de contenu et instanciez-le à l’aide de [`CoCreateInstanceFromApp`](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp) . Pour plus d’informations, consultez le billet de blog [Using Free-COM DLL in Windows Store C++ Project](/archive/blogs/win8devsupport/using-free-com-dll-in-windows-store-c-project).

Si vous souhaitez déplacer une bibliothèque COM existante vers UWP, il est également possible de la convertir en un composant Windows Runtime. Nous recommandons la bibliothèque C++/WinRT pour ces ports, mais il est également possible d’utiliser la [bibliothèque de modèles c++ Windows Runtime](../cppcx/wrl/windows-runtime-cpp-template-library-wrl.md). Le WRL est déconseillé et ne prend pas en charge toutes les fonctionnalités d’ATL et OLE. Le fait qu’un tel port soit possible dépend des fonctionnalités COM, ATL et OLE requises par votre composant.

Quel que soit le scénario de développement que vous choisissez, vous devez être conscient d’un certain nombre de définitions de macros. Vous pouvez utiliser ces macros dans votre code, pour compiler le code de façon conditionnelle sous le bureau classique Win32 et UWP.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Ces instructions s’appliquent respectivement aux applications UWP, aux applications du Windows Phone Store, aux deux ou bien aux applications de bureau Win32 classiques uniquement. Ces macros sont uniquement disponibles dans SDK Windows 8,1 et versions ultérieures.

Cet article contient les procédures suivantes :

- [Utilisation d’une DLL Win32 dans une application UWP](#BK_Win32DLL)

- [Utilisation d’une bibliothèque statique C++ native dans une application UWP](#BK_StaticLib)

- [Portage d’une bibliothèque C++ vers un composant Windows Runtime](#BK_WinRTComponent)

## <a name="using-a-win32-dll-in-a-uwp-app"></a><a name="BK_Win32DLL"></a> Utilisation d’une DLL Win32 dans une application UWP

Pour une sécurité et une fiabilité optimales, les applications Windows universelles s’exécutent dans un environnement d’exécution restreint. Vous ne pouvez pas simplement utiliser une DLL native comme vous le feriez dans une application de bureau Windows classique. Si vous disposez du code source pour une DLL, vous pouvez le déplacer de manière à ce qu'il s'exécute sur UWP. Commencez par modifier quelques paramètres du projet et les métadonnées du fichier projet pour identifier le projet en tant que projet UWP. Vous recompilerez le code de la bibliothèque à l’aide de l' `/ZW` option, qui active C++/CX. Certains appels d’API ne sont pas autorisés dans les applications UWP en raison de contrôles plus stricts associés à cet environnement. Pour plus d’informations, consultez [API Win32 et com pour les applications UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Si vous avez une DLL native qui exporte des fonctions à l’aide de `__declspec(dllexport)`, vous pouvez les appeler à partir d’une application UWP en recompilant la DLL en tant que projet UWP. Supposons, par exemple, que nous ayons un projet DLL Win32 nommé *Giraffe* qui exporte deux classes et leurs méthodes, avec du code similaire au fichier d’en-tête suivant :

```cpp
// giraffe.h
// Define GIRAFFE_EXPORTS when building this DLL
#pragma once

#ifdef GIRAFFE_EXPORTS
#define GIRAFFE_API __declspec(dllexport)
#else
#define GIRAFFE_API
#endif

GIRAFFE_API int giraffeFunction();

class Giraffe
{
    int id;
        Giraffe(int id_in);
    friend class GiraffeFactory;

public:
    GIRAFFE_API int GetID();
};

class GiraffeFactory
{
    static int nextID;

public:
    GIRAFFE_API GiraffeFactory();
    GIRAFFE_API static int GetNextID();
    GIRAFFE_API static Giraffe* Create();
};
```

Et le fichier de code suivant :

```cpp
// giraffe.cpp
#include "pch.h"
#include "giraffe.h"

Giraffe::Giraffe(int id_in) : id(id_in)
{
}

int Giraffe::GetID()
{
    return id;
}

int GiraffeFactory::nextID = 0;

GiraffeFactory::GiraffeFactory()
{
    nextID = 0;
}

int GiraffeFactory::GetNextID()
{
    return nextID;
}

Giraffe* GiraffeFactory::Create()
{
    return new Giraffe(nextID++);
}

int giraffeFunction();
```

Tout le reste dans le projet ( *`pch.h`* , *`dllmain.cpp`* ) fait partie du modèle de projet Win32 standard. Le code définit la macro `GIRAFFE_API` , qui correspond à `__declspec(dllexport)` lorsque `GIRAFFE_EXPORTS` est défini. Autrement dit, il est défini lorsque le projet est généré en tant que DLL, mais pas lorsqu’un client utilise l' *`giraffe.h`* en-tête. Cette DLL peut être utilisée dans un projet UWP sans modifier le code source. Seuls certains paramètres et propriétés du projet doivent être modifiés.

La procédure suivante s’applique quand vous avez une DLL native qui expose des fonctions à l’aide de `__declspec(dllexport)` .

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Pour porter une DLL native vers la plateforme UWP sans créer de projet

1. Ouvrez votre projet DLL dans Visual Studio.

1. Ouvrez les **Propriétés** du projet de la dll et définissez la **configuration** sur **toutes les configurations**.

1. Dans les **Propriétés du projet**, sous **C/C++** > onglet **Général**, affectez la valeur **Oui (/ZW)** à **Consommer l’extension Windows Runtime**. Cette propriété active les extensions de composant (C++/CX).

1. Dans **Explorateur de solutions**, sélectionnez le nœud du projet, ouvrez le menu contextuel, puis choisissez **décharger le projet**. Ensuite, ouvrez le menu contextuel sur le nœud du projet déchargé et choisissez de modifier le fichier projet. Localisez l’élément `WindowsTargetPlatformVersion`, et remplacez-le par les éléments suivants.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Fermez le *`.vcxproj`* fichier, rouvrez le menu contextuel, puis choisissez **recharger le projet**.

   **Explorateur de solutions** identifie désormais le projet en tant que projet Windows universel.

1. Assurez-vous que le nom de votre fichier d'en-tête précompilé est correct. Dans la section **en-têtes précompilés** , vous devrez peut-être modifier le **fichier d’en-tête précompilé** dans *`pch.h`* ou inversement *`stdafx.h`* si vous voyez une erreur semblable à celle-ci :

   > erreur C2857 : l’instruction' #include’spécifiée avec l' **`/Ycpch.h`** option de ligne de commande est introuvable dans le fichier source

   Le problème est que les modèles de projet plus anciens utilisent une convention d’affectation des noms différente pour le fichier d’en-tête précompilé. Les projets Visual Studio 2019 et versions ultérieures utilisent *`pch.h`* .

1. Créez le projet. Vous pouvez obtenir des erreurs sur les options de ligne de commande incompatibles. Par exemple, l’option fréquemment utilisée mais à présent dépréciée **Activer la régénération minimale (/Gm)** est définie par défaut dans de nombreux projets C++ plus anciens et est incompatible avec `/ZW`.

   Certaines fonctions ne sont pas disponibles lorsque vous compilez pour l’plateforme Windows universelle. Vous verrez des erreurs du compilateur concernant les problèmes éventuels. Résolvez ces erreurs jusqu’à ce que vous disposiez d’une génération propre.

1. Pour utiliser la dll dans une application UWP dans la même solution, ouvrez le menu contextuel du nœud de projet UWP, puis choisissez **Ajouter**une  >  **référence**.

   Sous **Projects**  >  **solution**de projets, activez la case à cocher en regard du projet dll, puis choisissez le bouton **OK** .

1. Incluez le ou les fichiers d’en-tête de la bibliothèque dans le fichier de votre application UWP *`pch.h`* .

    ```cpp
    #include "..\Giraffe\giraffe.h"
    ```

1. Ajoutez comme d'habitude du code dans le projet UWP pour appeler des fonctions et créer des types à partir de la DLL.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

## <a name="using-a-native-c-static-library-in-a-uwp-app"></a><a name="BK_StaticLib"></a> Utilisation d’une bibliothèque statique C++ native dans une application UWP

Vous pouvez utiliser une bibliothèque statique C++ native dans un projet UWP, mais vous devez tenir compte de certaines restrictions et limitations. Commencez par lire les informations relatives aux [bibliothèques statiques dans C++/CX](../cppcx/static-libraries-c-cx.md). Vous pouvez accéder au code natif dans votre bibliothèque statique à partir de votre application UWP, mais il n'est pas recommandé de créer des types ref publics dans une bibliothèque statique. Si vous compilez une bibliothèque statique avec l’option `/ZW`, le générateur de bibliothèques (en fait, l’éditeur de liens déguisé) émet un avertissement :

> LNK4264 : archivage du fichier objet compilé avec /ZW dans une bibliothèque statique ; notez qu’au moment de créer des types Windows Runtime, il est déconseillé d’établir une liaison avec une bibliothèque statique qui contient des métadonnées Windows Runtime

Toutefois, vous pouvez utiliser une bibliothèque statique dans une application UWP sans la recompiler avec `/ZW` . Votre bibliothèque ne peut pas déclarer de types ref ou utiliser des constructions C++/CX. Toutefois, si votre objectif est simplement d’utiliser une bibliothèque de code natif, vous pouvez le faire en suivant ces étapes.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Pour utiliser une bibliothèque statique C++ native dans un projet UWP

1. Dans les propriétés du projet pour le projet UWP, choisissez **Propriétés de configuration**  >  **Linker**  >  **entrée** de l’éditeur de liens dans le volet gauche. Dans le volet droit, ajoutez le chemin d’accès à la bibliothèque dans la propriété **Dépendances supplémentaires**. Par exemple, pour une bibliothèque dans le projet qui place sa sortie dans *`<SolutionFolder>\Debug\MyNativeLibrary\MyNativeLibrary.lib`* , ajoutez le chemin d’accès relatif *`Debug\MyNativeLibrary\MyNativeLibrary.lib`* .

1. Ajoutez une instruction include pour référencer le fichier d’en-tête dans votre *`pch.h`* fichier (le cas échéant), ou dans n’importe quel *`.cpp`* fichier si nécessaire, puis commencez à ajouter du code qui utilise la bibliothèque.

   ```cpp
   #include "..\MyNativeLibrary\MyNativeLibrary.h"
   ```

   N’ajoutez pas de référence dans le nœud **références** de **Explorateur de solutions**. Ce mécanisme fonctionne uniquement avec les composants Windows Runtime.

## <a name="porting-a-c-library-to-a-windows-runtime-component"></a><a name="BK_WinRTComponent"></a> Portage d’une bibliothèque C++ vers un composant Windows Runtime

Supposons que vous souhaitez consommer des API natives dans une bibliothèque statique à partir d’une application UWP. Si vous disposez du code source de la bibliothèque native, vous pouvez déplacer le code vers un composant Windows Runtime. Il ne s’agit plus d’une bibliothèque statique. vous allez le transformer en DLL que vous pouvez utiliser dans n’importe quelle application UWP C++. Cette procédure décrit comment créer un composant Windows Runtime qui utilise des extensions C++/CX. Pour plus d’informations sur la création d’un composant qui utilise C++/WinRT à la place, consultez [Windows Runtime Components with c++/WinRT](/windows/uwp/winrt-components/create-a-windows-runtime-component-in-cppwinrt).

Lorsque vous utilisez C++/CX, vous pouvez ajouter des types ref et d’autres constructions C++/CX, qui sont disponibles pour les clients dans n’importe quel code d’application UWP. Vous pouvez accéder à ces types à partir de C#, Visual Basic ou JavaScript. La procédure de base est la suivante :

- Créer un projet de composant Windows Runtime (Windows universel),
- Copiez le code de votre bibliothèque statique dans celui-ci, puis
- Résolvez les erreurs du compilateur provoquées par l' `/ZW` option.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Pour déplacer une bibliothèque C++ vers un composant Windows Runtime

1. Créez un projet de composant Windows Runtime (Windows universel).

1. Fermez le projet.

1. Dans l' **Explorateur de fichiers Windows**, localisez le nouveau projet. Ensuite, recherchez le projet de bibliothèque C++ qui contient le code que vous souhaitez porter. Copiez les fichiers sources (fichiers d’en-tête, fichiers de code et toute autre ressource, y compris dans les sous-répertoires) de votre projet de bibliothèque C++. Collez-les dans le nouveau dossier du projet en veillant à conserver la même structure de dossiers.

1. Rouvrez le projet de composant Windows Runtime. Ouvrez le menu contextuel du nœud de projet dans **Explorateur de solutions**, puis choisissez **Ajouter**un  >  **élément existant**.

1. Sélectionnez tous les fichiers à ajouter à partir de votre projet d’origine, puis choisissez **OK**. Répétez cette opération si nécessaire pour les sous-dossiers.

1. Il est possible que vous vous retrouviez avec du code dupliqué. S’il existe plusieurs en-têtes précompilés (par exemple, *`stdafx.h`* et *`pch.h`* ), choisissez-en un à conserver. Copiez tout le code requis, comme les instructions include, dans celui que vous souhaitez conserver. Ensuite, supprimez l’autre, puis dans les propriétés du projet, sous **en-têtes précompilés**, assurez-vous que le nom du fichier d’en-tête est correct.

   Si vous avez modifié le fichier à utiliser comme en-tête précompilé, assurez-vous que les options des en-têtes précompilés sont correctes pour chaque fichier. Sélectionnez chaque *`.cpp`* fichier à son tour, ouvrez sa fenêtre Propriétés et assurez-vous que tous sont définis sur **utiliser (/Yu)**, à l’exception de l’en-tête précompilé, qui doit être défini sur **créer (/YC)**.

1. Générez le projet et corrigez les erreurs. Ces erreurs peuvent être provoquées par l’utilisation de l' `/ZW` option, ou elles peuvent être provoquées par une nouvelle version du SDK Windows. Ils peuvent également refléter des dépendances telles que les fichiers d’en-tête dont votre bibliothèque dépend ou des différences dans les paramètres de projet entre votre ancien projet et le nouveau.

1. Ajoutez des types ref publics à votre projet ou convertissez des types ordinaires en types ref. Utilisez ces types pour exposer des points d’entrée dans les fonctionnalités que vous souhaitez appeler à partir d’applications UWP.

1. Testez le composant en ajoutant une référence à celui-ci à partir d'un projet d'application UWP et ajoutez du code pour appeler les API publiques que vous avez créées.

## <a name="see-also"></a>Voir aussi

[Portage vers la plateforme universelle Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)
