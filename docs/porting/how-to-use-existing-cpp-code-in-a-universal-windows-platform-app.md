---
title: Guide pratique pour utiliser le code C++ existant dans une application de plateforme universelle Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3f8cb26a66fce9c4b87822ffbfa4005f3a2e758
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847970"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Comment : utiliser le code C++ existant dans une application pour la plateforme Windows universelle
Le moyen le plus simple d’exécuter votre programme de bureau dans l’environnement UWP consiste peut-être à utiliser les technologies de pont de bureau. Elles incluent Desktop App Converter, qui va empaqueter votre application existante comme application UWP sans nécessiter de modifications de code. Pour plus d’informations, consultez [Déplacer votre application de bureau vers la plateforme universelle Windows (UWP) avec le pont du bureau](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root).

Le reste de cette rubrique explique comment déplacer les bibliothèques C++ (DLL et bibliothèques statiques) vers la plateforme universelle Windows (UWP). Cette procédure peut vous être utile pour que votre logique C++ principale puisse être utilisée avec plusieurs applications UWP. 
  
 Les applications UWP s'exécutent dans un environnement protégé. Par conséquent, de nombreux appels d'API Win32, COM et CRT qui peuvent compromettre la sécurité de la plateforme ne sont pas autorisés. Si l'option /ZW est utilisée, le compilateur peut détecter de tels appels et générer une erreur. Vous pouvez utiliser le Kit de certification des applications sur votre application pour détecter le code qui appelle des API interdites. Consultez [Utilisation du Kit de certification des applications Windows](https://msdn.microsoft.com/library/windows/apps/hh694081.aspx).  
  
 Si le code source est disponible pour la bibliothèque, il est possible que vous puissiez éliminer les appels d'API interdits. Pour obtenir plus de détails, notamment la liste des API autorisées et interdites, consultez [Win32 et COM pour les applications Windows Runtime et les applications de plateforme Windows universelle (UWP)](https://msdn.microsoft.com/library/windows/apps/br205762.aspx) et [Fonctions CRT non prises en charge dans les applications de plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Des alternatives sont disponibles dans [Alternatives aux API Windows dans les applications UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).  
  
 Si vous essayez simplement d'ajouter une référence d'un projet Windows universel à une bibliothèque de bureau classique, vous obtenez un message d'erreur indiquant que la bibliothèque n'est pas compatible. Dans le cas d'une bibliothèque statique, vous pouvez établir un lien à votre bibliothèque en ajoutant simplement la bibliothèque (fichier .lib) à l'entrée de votre éditeur de liens, comme dans le cas d'une application Win32 classique. Pour les bibliothèques où seul un binaire est disponible, il n'y a pas d'autre option. Une bibliothèque statique est liée dans le fichier exécutable de votre application, mais une DLL Win32 que vous consommez dans une application UWP doit être empaquetée dans l'application. Pour cela, vous devez l'inclure dans le projet et la marquer comme du contenu. Pour charger une DLL Win32 dans une application UWP, vous devez également appeler [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159.aspx) à la place de LoadLibrary ou de LoadLibraryEx.  
  
 Si vous disposez du code source pour la DLL ou la bibliothèque statique, vous pouvez le recompiler avec l'option /ZW en tant que projet UWP. Si vous procédez ainsi, vous pouvez ajouter une référence à l'aide de l'Explorateur de solutions et l'utiliser dans les applications UWP C++. Dans le cas d'une DLL, vous établissez un lien avec la bibliothèque d'exportation.  
  
 Pour exposer des fonctionnalités aux appelants dans d'autres langages, vous pouvez convertir la bibliothèque en composant Windows Runtime. Les composants Windows Runtime diffèrent des DLL ordinaires en ce sens qu'ils incluent des métadonnées sous la forme de fichiers .winmd qui décrivent le contenu conformément aux exigences des consommateurs .NET et JavaScript. Pour exposer les éléments d’API à d’autres langages, vous pouvez ajouter des constructions C++/CX, telles que des classes ref, et les rendre publiques. Vous pouvez également utiliser la [bibliothèque de modèles C++ Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  Dans Windows 10 et versions ultérieures, vous pouvez utiliser la [bibliothèque C++/WinRT](https://github.com/microsoft/cppwinrt) au lieu de C++/CX. 
  
 La discussion précédente ne s'applique pas aux composants COM, car ceux-ci doivent être gérés différemment. Si vous disposez d’un serveur COM dans un fichier EXE ou DLL, vous pouvez l’utiliser dans un projet Windows universel. Pour cela, vous devez l’empaqueter en tant que [composant COM sans inscription](https://msdn.microsoft.com/library/dd408052.aspx), l’ajouter à votre projet en tant que fichier de contenu et l’instancier à l’aide de [CoCreateInstanceFromApp](https://msdn.microsoft.com/library/windows/apps/hh404137.aspx). Consultez [Using Free-COM DLL in Windows Store C++ Project](http://blogs.msdn.com/b/win8devsupport/archive/2013/05/20/using-free-com-dll-in-windows-store-c-project.aspx).  
  
 Si vous avez une bibliothèque COM existante que vous souhaitez déplacer vers la plateforme UWP, vous pouvez peut-être la convertir en composant Windows Runtime à l’aide de la [bibliothèque de modèles C++ Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). La bibliothèque WRL ne prend pas en charge toutes les fonctionnalités offertes par ATL et OLE. Vous devez donc examiner dans quelle mesure votre code COM dépend des fonctionnalités COM, ATL, et OLE requises par votre composant pour déterminer si ce déplacement est faisable.  
  
 Plusieurs méthodes permettent d’utiliser du code C++ existant dans les projets UWP. Certaines nécessitent que le code soit recompilé avec les extensions du composant (C++/CX) activées (autrement dit, avec l'option /ZW), d'autres pas. Par conséquent, si vous devez conserver le code en C++ standard ou maintenir un environnement de compilation Win32 classique pour une partie du code, vous pouvez le faire avec une architecture appropriée. Par exemple, tout le code contenant l'interface utilisateur UWP et les types à exposer aux appelants C#, Visual Basic et JavaScript doit figurer dans des projets d'application Windows et des projets de composant Windows Runtime. Le code qui doit être consommé uniquement dans C++ (y compris C++/CX) peut figurer soit dans un projet qui compile avec l'option /WX, soit dans un projet C++ standard. Vous pouvez utiliser le code binaire uniquement en le liant en tant que bibliothèque statique. Vous pouvez aussi l'empaqueter avec l'application en tant que contenu et le charger dans une DLL uniquement s'il n'utilise pas les API interdites.  
  
 Quel que soit le scénario de développement que vous choisissez, vous devez connaître un certain nombre de définitions de macros à utiliser dans votre code pour le compiler de manière conditionnelle (sur la plateforme de bureau Win32 classique et la plateforme UWP).  
  
```cpp  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
```  
  
 Ces instructions s’appliquent respectivement aux applications UWP, aux applications du Windows Phone Store, aux deux ou bien aux applications de bureau Win32 classiques uniquement. Ces macros sont uniquement disponibles dans le Kit de développement logiciel (SDK) Windows 8.1 et versions ultérieures. Par conséquent, si votre code doit être compilé avec des versions antérieures du SDK Windows ou pour d’autres plateformes non-Windows, vous devez également vous préparer à l’éventualité qu’aucune de ces macros ne soit définie.  
  
 Cette rubrique contient les procédures suivantes.  
  
1.  [Utilisation d’une DLL Win32 dans une application UWP](#BK_Win32DLL)  
  
2.  [Utilisation d’une bibliothèque statique C++ native dans une application UWP](#BK_StaticLib)  
  
3.  [Portage d’une bibliothèque C++ vers un composant Windows Runtime](#BK_WinRTComponent)  
  
##  <a name="BK_Win32DLL"></a> Utilisation d’une DLL Win32 dans une application UWP  
 Pour renforcer la sécurité et la fiabilité, les applications pour la plateforme Windows universelle s'exécutent dans un environnement d'exécution restreint. Vous ne pouvez donc pas utiliser n'importe quelle DLL native comme vous le feriez dans une application de bureau Windows classique. Si vous disposez du code source pour une DLL, vous pouvez le déplacer de manière à ce qu'il s'exécute sur UWP. Commencez par modifier quelques paramètres du projet et les métadonnées du fichier projet pour identifier le projet en tant que projet UWP. Vous devez compiler le code de bibliothèque à l'aide de l'option /ZW, ce qui permet d'activer C++/CX. Certains appels d'API ne sont pas autorisés dans les applications UWP en raison des contrôles plus stricts associés à cet environnement. Consultez [Win32 et COM pour les applications Windows Runtime et les applications de plateforme universelle Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
 La procédure suivante s'applique quand vous avez une DLL native qui expose des fonctions à l'aide de __declspec(dllexport).  
  
#### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Pour porter une DLL native vers la plateforme UWP sans créer de projet  
  
1.  Si vous avez une DLL native qui exporte des fonctions à l'aide de __declspec(dllexport), vous pouvez appeler ces fonctions à partir d'une application UWP en recompilant la DLL comme projet UWP. Par exemple, supposons que nous avons une DLL qui exporte deux classes et leurs méthodes, avec du code semblable au fichier d'en-tête suivant :  
  
    ```  
    // giraffe.h  
    #pragma once  
  
    #ifdef _DLL  
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
  
    ```  
    // giraffe.cpp  
    #include "stdafx.h"  
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
  
     Tout le reste dans le projet (stdafx.h, dllmain.cpp) fait partie du modèle de projet Win32 standard. Si vous souhaitez poursuivre, mais sans utiliser votre propre DLL durant ces étapes, essayez de créer un projet Win32, sélectionnez DLL dans l'Assistant de projet, ajoutez un en-tête de fichier giraffe.h et un fichier de code giraffe.cpp, puis copiez le contenu du code de cette étape dans les fichiers appropriés.  
  
     Le code définit la macro GIRAFFE_API qui est résolue en __declspec(dllexport) quand _DLL est défini (autrement dit, quand le projet est créé en tant que DLL).  
  
2.  Ouvrez les propriétés du projet de DLL et affectez la valeur **Toutes les configurations** à Configuration.  
  
3.  Dans les propriétés du projet, sous **C/C++**, onglet **Général**, affectez la valeur **Oui (/ZW)** à **Consommer l’extension Windows Runtime**. Cette opération active les extensions du composant (C++/CX).  
  
4.  Dans l’**Explorateur de solutions**, sélectionnez le nœud du projet, ouvrez le menu contextuel et choisissez **Décharger le projet**. Ensuite, ouvrez le menu contextuel sur le nœud du projet déchargé et choisissez de modifier le fichier projet. Recherchez l'élément WindowsTargetPlatformVersion et remplacez-le par les éléments suivants.  
  
    ```xml  
    <AppContainerApplication>true</AppContainerApplication>  
    <ApplicationType>Windows Store</ApplicationType>  
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>  
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>  
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
    ```  
  
     Fermez le fichier .vcxproj, rouvrez le menu contextuel et choisissez **Recharger le projet**.  
  
     L'Explorateur de solutions identifie désormais le projet comme projet d'application Windows universelle.  
  
5.  Assurez-vous que le nom de votre fichier d'en-tête précompilé est correct. Dans la section En-têtes précompilés, remplacez le fichier d'en-tête précompilé pch.h par stdafx.h. Si vous ne le faites pas, l'erreur suivante apparaît.  
  
    ```Output  
    error C2857: '#include' statement specified with the /Ycpch.h command-line option was not found in the source file  
    ```  
  
     Le problème est que les projets d’application Windows universelle utilisent une convention d’affectation des noms différente pour le fichier d’en-tête précompilé.  
  
6.  Générez le projet. Vous pouvez obtenir des erreurs qui découlent d'options de ligne de commande incompatibles. Par exemple, l'option Activer la régénération minimale (/Gm) fréquemment utilisée est définie par défaut dans de nombreux projets C++ et n'est pas compatible avec /ZW.  
  
     Certaines fonctions ne sont pas disponibles quand vous compilez pour la plateforme Windows universelle. Le compilateur génère des erreurs chaque fois qu'un problème se produit. Résolvez-les jusqu'à obtenir une build propre.  
  
7.  Pour utiliser la DLL dans une application UWP dans la même solution, ouvrez le menu contextuel du nœud de projet UWP et choisissez **Ajouter, Référence**.  
  
     Sous **Projets, Solution**, cochez la case en regard du projet de DLL et choisissez le bouton **OK**.  
  
8.  Incluez le ou les fichiers d’en-tête de la bibliothèque dans le fichier pch.h de votre application UWP.  
  
    ```  
    #include "..\MyNativeDLL\giraffe.h"  
    ```  
  
9. Ajoutez comme d'habitude du code dans le projet UWP pour appeler des fonctions et créer des types à partir de la DLL.  
  
    ```  
    MainPage::MainPage()  
    {  
        InitializeComponent();  
        GiraffeFactory gf;  
        Giraffe* g = gf.Create();  
        int id = g->GetID();  
    }  
  
    ```  
  
##  <a name="BK_StaticLib"></a> Utilisation d’une bibliothèque statique C++ native dans une application UWP  
 Vous pouvez utiliser une bibliothèque statique C++ native dans un projet UWP, mais vous devez tenir compte de certaines restrictions et limitations. Commencez par lire cette [rubrique](https://msdn.microsoft.com/library/hh771041.aspx) sur les bibliothèques statiques dans C++/CX. Vous pouvez accéder au code natif dans votre bibliothèque statique à partir de votre application UWP, mais il n'est pas recommandé de créer des types ref publics dans une bibliothèque statique. Si vous compilez une bibliothèque statique avec l'option /ZW, le générateur de bibliothèques (en fait l'éditeur de liens déguisé) émet un avertissement :  
  
```  
LNK4264: archiving object file compiled with /ZW into a static library; note that when authoring Windows Runtime types it is not recommended to link with a static library that contains Windows Runtime metadata  
```  
  
 Toutefois, vous pouvez utiliser une bibliothèque statique dans une application UWP sans la recompiler avec /ZW. Vous ne pouvez ni déclarer des types ref ni utiliser des constructions C++/CX. Toutefois, si votre objectif est simplement d'utiliser la bibliothèque de code natif, vous pouvez le faire en suivant ces étapes.  
  
#### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Pour utiliser une bibliothèque statique C++ native dans un projet UWP  
  
1.  Dans les propriétés du projet pour le projet UWP, dans la section Éditeur de liens, ajoutez le chemin d’accès à la bibliothèque dans la propriété Entrée. Par exemple, pour une bibliothèque dans le projet qui place sa sortie dans *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, ajoutez le chemin d’accès relatif `Debug\MyNativeLibrary\MyNativeLibrary.lib`.  
  
2.  Ajoutez une instruction include pour référencer le fichier d’en-tête à votre fichier pch.h dans le projet UWP, puis commencez à ajouter du code qui utilise la bibliothèque.  
  
    ```  
    #include "..\MyNativeLibrary\giraffe.h"  
    ```  
  
     N’ajoutez pas de référence dans le nœud **Références** de l’**Explorateur de solutions**. Ce mécanisme fonctionne uniquement avec les composants Windows Runtime.  
  
##  <a name="BK_WinRTComponent"></a> Portage d’une bibliothèque C++ vers un composant Windows Runtime  
 Si vous souhaitez consommer des API natives dans une bibliothèque statique à partir d'une application UWP et que vous disposez du code source de la bibliothèque native, vous pouvez déplacer le code vers un composant Windows Runtime. Dans ce cas, il ne s'agit plus d'une bibliothèque statique, mais d'une DLL. Vous pouvez l'utiliser dans n'importe quelle application UWP C++, mais contrairement au scénario de bibliothèque statique, vous pouvez ajouter des types ref et d'autres constructions C++/CX qui sont accessibles aux clients dans n'importe quel code d'application UWP, indépendamment du langage. Par conséquent, vous pouvez accéder à ces types à partir de code C#, Visual Basic ou JavaScript.  La procédure de base est la suivante : créez un projet de composant Windows Runtime, copiez le code de votre bibliothèque statique dans ce projet, puis corrigez les erreurs provoquées par le déplacement du code d'une compilation C++ standard vers une compilation /ZW.  
  
#### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Pour déplacer une bibliothèque C++ vers un composant Windows Runtime  
  
1.  Créez un projet de composant Windows Runtime.  
  
2.  Fermez le projet.  
  
3.  Dans l'Explorateur de fichiers Windows, recherchez le projet. Par défaut, Visual Studio utilise le dossier Visual Studio 2017\Projects dans votre dossier Documents. Recherchez le projet de bibliothèque C++ contenant le code que vous souhaitez déplacer. Copiez les fichiers de code source (fichiers d'en-tête, fichiers de code et toute autre ressource, y compris dans les sous-répertoires) de votre projet de bibliothèque C++, puis collez-les dans le dossier du projet en veillant à conserver la même structure de dossiers.  
  
4.  Rouvrez le projet de composant Windows Runtime, ouvrez le menu contextuel du nœud de projet dans l’**Explorateur de solutions**, puis choisissez **Ajouter, Élément existant**.  
  
5.  Sélectionnez tous les fichiers à ajouter de votre projet d'origine, puis cliquez sur OK. Répétez cette opération si nécessaire pour les sous-dossiers.  
  
6.  Il est possible que vous vous retrouviez avec du code dupliqué. Si vous disposez de plusieurs en-têtes précompilés (par exemple, stdafx.h et pch.h), choisissez-en un. Copiez tout le code requis, comme les instructions include, dans celui que vous souhaitez conserver. Supprimez ensuite l’autre et, dans les propriétés du projet, sous **En-têtes précompilés**, vérifiez que le nom du fichier d’en-tête est correct.  
  
     Si vous avez modifié le fichier à utiliser comme en-tête précompilé, assurez-vous que les options des en-têtes précompilés sont correctes pour chaque fichier. Sélectionnez un à un les fichiers .cpp, ouvrez la fenêtre de propriétés de chacun d’eux et vérifiez que toutes les propriétés ont la valeur **Utiliser (/Yu)**, à l’exception de l’en-tête précompilé voulu qui doit avoir la valeur **Créer (/Yc)**.  
  
7.  Générez le projet et corrigez les erreurs. Ces erreurs peuvent être causées par l'utilisation de l'option /ZW ou par une nouvelle version du SDK Windows. Elles peuvent aussi refléter des dépendances, comme la dépendance de votre bibliothèque vis-à-vis des fichiers d'en-tête, ou des différences au niveau des paramètres entre votre ancien projet et le nouveau.  
  
8.  Ajoutez des types ref publics à votre projet ou convertissez des types ordinaires en types ref pour exposer des points d'entrée dans les fonctionnalités que vous souhaitez appeler à partir d'applications UWP.  
  
9. Testez le composant en ajoutant une référence à celui-ci à partir d'un projet d'application UWP et ajoutez du code pour appeler les API publiques que vous avez créées.  
  
## <a name="see-also"></a>Voir aussi  
 [Portage vers la plateforme universelle Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)