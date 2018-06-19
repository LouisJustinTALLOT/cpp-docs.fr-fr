---
title: Vue d’ensemble de la programmation Windows en C++ | Documents Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2096c36ec24c1ca7e20c789b8a1eb8c24589ccc1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881661"
---
# <a name="overview-of-windows-programming-in-c"></a>Vue d'ensemble de la programmation Windows en C++

Vous pouvez utiliser Visual C++ pour écrire de nombreux types de programmes qui s’exécutent sur un PC Windows (x 86, x64 ou ARM), sur un serveur Windows, dans le cloud ou sur Xbox. Les programmes C++ bien écrits ont ces caractéristiques :
- efficace dans les besoins en mémoire
- économes en énergie 
- la possibilité de tirer pleinement parti des périphériques, voire de nombreux cœurs
- en mesure d’effectuer un calcul général sur l’unité de traitement graphique (GPGPU)   
- la possibilité de tirer parti des autres avancées récentes dans le matériel.

Il existe plusieurs grandes catégories d'applications Windows que vous pouvez développer avec Visual C++. Ces catégories ont des modèles de programmation différents ou des modèles d’application, qui ont été introduites au fil des années. Chaque modèle utilise différentes bibliothèques et API pour fournir l’accès à la plateforme et de créer des interfaces utilisateur telles que les fenêtres et boîtes de dialogue. La bibliothèque C++ standard, ainsi que des bibliothèques tierces peuvent servir dans un de ces catégories, avec quelques restrictions pour la plateforme Windows universelle.

- [Applications Windows universelles](#BK_WindowsUniversal). La troisième catégorie d'applications Windows a été introduite avec Windows 8 et la prise en charge de cette catégorie continue dans Windows 10. Ces applications sont souvent appelées simplement « applications Windows » et elles incluent des applications mobiles et de bureau qui ciblent divers appareils. Vous pouvez écrire ces applications en C++/CX, un dialecte de C++ qui inclut la prise en charge du développement Windows Runtime, ou en C++ standard avec COM qui utilise la bibliothèque WRL (Windows Runtime Library). Ces applications ont été conçues initialement pour s'exécuter en mode plein écran, bien que les utilisateurs de Windows 10 aient la possibilité de les exécuter dans une fenêtre du bureau. Elles intègrent des fonctions tactiles, mais il est facile d'utiliser la souris pour les faire fonctionner si les utilisateurs le préfèrent ou en l'absence d'un écran tactile. Ces applications sont distribuées à partir du Store de Microsoft, ce qui a conduit à les appeler les applications « Store ».

Les applications UWP soient en mesure d’exécuter sur tous les appareils Windows 10 tels que les tablettes et téléphones mobiles, ainsi que sur le bureau. Sur le bureau, elles peuvent s'exécuter sous la forme d'une fenêtre du bureau au lieu de toujours s'exécuter en mode plein écran. Ces applications peuvent également s'exécuter sur la Xbox et sur les appareils futurs.  Les applications UWP s’exécutent sur le Windows Runtime, qui fournit une interface pour les divers périphériques matériels qui sont pris en charge sur Windows, des services et des éléments d’interface utilisateur.  

Vous pouvez écrire des applications UWP dans C + c++ / CX, un dialecte de C++, vous pouvez utiliser la [C + c++ / bibliothèque WinRT](https://moderncpp.com/)pour certains scénarios. Les applications UWP compilent en code natif et une interface utilisateur XAML ou utilisent DirectX. Composants Windows Runtime qui sont écrits en code natif que les applications UWP écrites dans d’autres langages peuvent consommer. Pour plus d’informations, consultez [créer une application de plateforme Windows universelle en C++](http://go.microsoft.com/fwlink/?LinkID=534976), [créer votre premier jeu de plateforme Windows universelle à l’aide de DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656), et [des composants de création de Windows Runtime en C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).

   Cette catégorie inclut également l'utilisation de C++ pour les composants principaux et le code de calcul dans le contexte de la programmation serveur et cloud. Parfois, le code exigeant en performances situé au cœur d'une application serveur ou cloud est écrit en C++ pour optimiser les performances. Vous pouvez compiler ce code dans une DLL et l'utiliser à partir de C# ou de Visual Basic.

- **Applications .NET Framework**. La plupart des applications .NET Framework sont écrites en C# ou Visual Basic, mais elles peuvent également l'être en C++/CLI (option de compilateur /clr dans Visual C++). Nous vous recommandons d'utiliser C++/CLI pour une couche d'interopérabilité minimale dans une application plus importante qui inclut du code managé et natif.

##  <a name="BK_WindowsUniversal"></a> Windows Universal Apps

Avec Windows 10, les applications peuvent s'exécuter sur tous les appareils Windows 10, tels que les tablettes et les téléphones mobiles, ainsi que sur le bureau. Sur le bureau, elles peuvent s'exécuter sous la forme d'une fenêtre du bureau au lieu de toujours s'exécuter en mode plein écran. Ces applications peuvent également s'exécuter sur la Xbox et sur les appareils futurs.  Le modèle de programmation utilisé pour ces deux types d'applications est différent de celui utilisé pour les applications de bureau Win32. Ces applications Windows s'exécutent sur le Windows Runtime, qui fournit les éléments d'interface utilisateur, les services essentiels pour ces applications, ainsi qu'une interface pour les divers périphériques matériels pris en charge. Ces applications sont compilées en code natif et possèdent une interface utilisateur XAML, ou utilisent DirectX. Vous pouvez également écrire des composants Windows Runtime en code natif qui consomment les autres applications Windows, notamment les applications qui sont écrites en c#, Visual Basic ou JavaScript. Pour plus d’informations, consultez [créer une application « Hello world » de plateforme Windows universelle en C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp), [créer un jeu UWP simple avec DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game), et [des composants de création de Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

> [!TIP]
> Pour Windows 10, vous pouvez utiliser le convertisseur d’application de bureau pour empaqueter votre application de bureau existante pour le déploiement via Microsoft Store. Pour plus d’informations, consultez [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) et [Déplacer votre application de bureau vers la plateforme universelle Windows (UWP) avec le pont du bureau](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).

Pour obtenir des exemples pour la plateforme Windows universelle, consultez les [exemples Windows universels sur GitHub](https://github.com/Microsoft/Windows-universal-samples)

Si vous avez un projet de Windows 8.1 et voulez le porter vers Windows 10 existants, consultez [portage vers la plateforme Windows universelle](../porting/porting-to-the-universal-windows-platform-cpp.md). Si vous avez existant de bibliothèques de bureau Win32 classiques et le code que vous souhaitez intégrer dans une application UWP, consultez [Comment : utiliser le Code C++ existant dans une application de plateforme Windows universelle](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

Pour plus d’informations sur la plateforme Windows universelle en général, consultez [qu’est une application de plateforme Windows universelle (UWP) ?](/windows/uwp/get-started/whats-a-uwp).

Pour plus d’informations sur l’ensemble de ces concepts, consultez [Guide pour les applications Windows universelles](http://go.microsoft.com/fwlink/p/?linkid=534605).

##  <a name="BK_Native"></a> Applications de bureau et serveur

Pour connaître les principes de base de la création d’applications clientes Windows pour le bureau, consultez [Developing Windows Applications in C++](http://msdn.microsoft.com/vstudio//hh304489) (Développement d’applications Windows utilisant C++) et [Introduction to Windows Programming in C++](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx)(Introduction à la programmation Windows en C++).

Sur Windows 10, vous pouvez utiliser Visual C++ pour créer de nombreux types de programmes de bureau :

- Applications et utilitaires en ligne de commande. Pour plus d’informations, consultez [Applications Console](../windows/console-applications-in-visual-cpp.md).

- Applications grand public dotées d'interfaces graphiques utilisateur sophistiquées. Pour plus d’informations, consultez [Hilo: Developing C++ Applications for Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417)(Hilo : développement d’applications C++ pour Windows)

- Applications de métier et d’entreprise qui s’exécutent sur le .NET Framework. La plupart des applications .NET Framework sont écrites en c# ou Visual Basic. Vous pouvez utiliser c++ / CLI pour créer des couches d’interopérabilité qui permettent au code .NET consommer des bibliothèques natives C++. Pour plus d’informations, consultez [programmation .NET avec C++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

- Clients de base de données SQL qui s'exécutent en code natif. Pour plus d’informations, consultez [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

- Compléments pour les applications Microsoft Office. Pour plus d’informations, consultez [Génération d’un complément C++ pour Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420)

- Pilotes de périphérique. Pour plus d’informations, consultez [Windows Driver Kit (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)

- Les services Windows. Pour plus d'informations, consultez [Introduction to Windows Service Applications](/dotnet/framework/windows-services/introduction-to-windows-service-applications).

Vous pouvez utiliser Visual C++ pour empaqueter quasiment tout type de fonctionnalité personnalisée à hautes performances dans des DLL Win32 ou dans des DLL COM qui peuvent être utilisées par les applications C++ ou par des applications écrites dans d'autres langages, tels que C# ou Visual Basic. Pour plus d’informations sur les DLL Win32, consultez [DLLs in Visual C++](../build/dlls-in-visual-cpp.md). Pour plus d’informations sur le développement COM, consultez [modèle COM (Component Object)](https://msdn.microsoft.com/library/windows/desktop/ms680573).

## <a name="games"></a>Jeux

Jeux DirectX peuvent s’exécuter sur le PC ou Xbox. Pour plus d’informations, consultez le [Centre de développement DirectX](http://go.microsoft.com/fwlink/p/?LinkId=256418).

## <a name="sdks-libraries-and-header-files"></a>Kits de développement logiciel, les bibliothèques et les fichiers d’en-tête

Visual C++ inclut la bibliothèque Runtime C (CRT), de la bibliothèque Standard C++ et d’autres bibliothèques spécifiques de Microsoft. Les dossiers include qui contiennent les fichiers d’en-tête de ces bibliothèques sont situés soit dans le répertoire d’installation de Visual Studio dans le dossier \VC\, ou dans le cas de la bibliothèque CRT, dans le dossier d’installation du SDK Windows.   

Vous pouvez utiliser la [Gestionnaire de package Vcpkg](../vcpkg.md) facilement installer des centaines de bibliothèques open source de tiers pour Windows.

Les bibliothèques Microsoft incluent :

- Bibliothèque MFC (Microsoft Foundation Classes) : infrastructure orientée objet conçue pour la création de programmes Windows traditionnels (notamment des applications d’entreprise) qui possèdent des interfaces utilisateur riches dotées de boutons, de zones de liste, d’arborescences et d’autres contrôles. Pour plus d'informations, consultez [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Bibliothèque ATL (Active Template Library) : bibliothèque d'assistance puissante pour créer des composants COM. Pour plus d'informations, consultez [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism) : bibliothèque qui permet un travail de calcul général à hautes performances sur le GPU. Pour plus d'informations, consultez [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime d'accès concurrentiel : bibliothèque qui simplifie le travail de programmation parallèle et asynchrone pour les appareils dotés de plusieurs cœurs, voire de nombreux cœurs. Pour plus d'informations, consultez [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

De nombreux scénarios de programmation Windows requièrent également le Kit de développement logiciel Windows, qui inclut les fichiers d'en-tête qui permettent l'accès aux composants du système d'exploitation Windows. Par défaut, Visual Studio installe le Kit de développement logiciel Windows en tant que composant de la charge de travail de bureau C++, ce qui permet de développer des applications Windows universelles. Pour développer des applications UWP, vous avez besoin de la version de Windows 10 du Kit de développement. Pour plus d’informations, consultez [SDK Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Pour plus d’informations sur les kits de développement logiciel Windows pour les versions antérieures de Windows, consultez le [archive du Kit de développement logiciel Windows](https://developer.microsoft.com/windows/downloads/sdk-archive)). 

**Programmer des fichiers (x86) \Windows Kits** est l’emplacement par défaut pour toutes les versions du Kit de développement que vous avez installée.

D'autres plateformes, telles que Xbox et Azure, possèdent leurs propres Kits de développement logiciel que vous pouvez être amené à installer. Pour plus d'informations, consultez le Centre de développement DirectX et le Centre de développement Azure.

## <a name="development-tools"></a>Outils de développement

Visual Studio inclut un débogueur puissant pour le code natif, des outils d’analyse statique, des outils de débogage graphique, un éditeur de code complet, la prise en charge des tests unitaires et de nombreux autres outils et utilitaires. Pour plus d’informations, consultez [prise en main du développement avec Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), et [IDE et outils de développement](../ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Rubrique parente pour le contenu du développeur Visual C++.|
