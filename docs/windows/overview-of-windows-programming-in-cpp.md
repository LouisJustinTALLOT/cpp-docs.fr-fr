---
title: Vue d'ensemble de la programmation Windows en C++
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 8ab7fbf7c955b1c828ef583aa639eda7409cf167
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359945"
---
# <a name="overview-of-windows-programming-in-c"></a>Vue d'ensemble de la programmation Windows en C++

Il existe plusieurs grandes catégories d’applications Windows que vous pouvez créer avec C. Chacune a son propre modèle de programmation et un ensemble de bibliothèques spécifiques à Windows, mais la bibliothèque standard de CMD et les bibliothèques CMD de tiers peuvent être utilisées dans n’importe lequel d’entre elles.

Cette section discute de la façon d’utiliser Visual Studio et les bibliothèques d’emballage MFC/ATL pour créer des programmes Windows. Pour la documentation sur la plate-forme Windows elle-même, voir [la documentation Windows](/windows/index).

## <a name="command-line-console-applications"></a>Applications de ligne de commande (console)

Les applications de consoleS CMD s’exécutent à partir de la ligne de commande dans une fenêtre de console et peuvent afficher la sortie de texte seulement. Pour plus d’informations, consultez [le projet d’application console CMD](../get-started/tutorial-console-cpp.md).

## <a name="native-desktop-client-applications"></a>Applications de clients de bureau natives

Une *application de client de bureau native* est une application fenêtre C ou CMD qui utilise les [API Ou composants (COM)](/windows/win32/apiindex/windows-api-list) natifs d’origine pour accéder au système d’exploitation. Ces API sont elles-mêmes écrites principalement en C. Il y a plus d’une façon de créer une application de bureau native : vous pouvez programmer directement en utilisant les API Win32, en utilisant une boucle de message de type C qui traite les événements du système d’exploitation. Ou, vous pouvez programmer à l’aide *de Microsoft Foundation Classes* (MFC), une bibliothèque CMD légèrement orientée vers les objets qui enveloppe Win32. Ni l’une ni l’autre approche n’est considérée comme «moderne» par rapport à la plate-forme Windows universelle (UWP), mais les deux sont encore entièrement pris en charge et ont des millions de lignes de code en cours d’exécution dans le monde d’aujourd’hui. Une application Win32 qui s’exécute dans une fenêtre exige que le développeur fonctionne explicitement avec des messages Windows à l’intérieur d’une fonction de procédure Windows. Malgré le nom, une application Win32 peut être compilée comme un binaire 32 bits (x86) ou 64 bits (x64). Dans le Visual Studio IDE, les termes x86 et Win32 sont synonymes.

Pour commencer avec la programmation traditionnelle de Windows CMD, voir [Get Started with Win32 et CMD](/windows/win32/LearnWin32/learn-to-program-for-windows). Après avoir obtenu une certaine compréhension de Win32, il sera plus facile d’en apprendre davantage sur [MFC Desktop Applications](../mfc/mfc-desktop-applications.md). Pour un exemple d’application de bureau CMD traditionnelle qui utilise des graphiques sophistiqués, voir [Hilo: Developing CMD Applications for Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C ou .NET?

En général, la programmation .NET en C est moins complexe, moins sujette aux erreurs, et a une API plus moderne orientée objet que Win32 ou MFC. Dans la plupart des cas, ses performances sont plus qu’adéquates. .NET dispose de la Windows Presentation Foundation (WPF) pour les graphismes riches, et vous pouvez consommer à la fois Win32 et l’API Windows Runtime moderne. En règle générale, nous vous recommandons d’utiliser CMD pour les applications de bureau lorsque vous avez besoin :

- contrôle précis de l’utilisation de la mémoire
- la plus grande économie de la consommation d’énergie
- utilisation du GPU pour l’informatique générale
- accès à DirectX
- utilisation intensive des bibliothèques standard de C

Il est également possible de combiner la puissance et l’efficacité de la programmation .NET. Vous pouvez créer une interface utilisateur dans le C et utiliser le CMD/CLI pour permettre à l’application de consommer des bibliothèques CMD natives. Pour plus d’informations, voir [.NET Programmation avec C '/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Composants COM

Le [modèle d’objet de composants (COM)](/windows/win32/com/the-component-object-model) est une spécification qui permet aux programmes écrits dans différentes langues de communiquer entre eux. De nombreux composants Windows sont implémenté comme objets COM et suivent les règles COM standard pour la création d’objets, la découverte d’interfaces et la destruction d’objets.  L’utilisation d’objets COM à partir d’applications de bureau C est relativement simple, mais l’écriture de votre propre objet COM est plus avancée. La [Bibliothèque Active Template (ATL)](../atl/atl-com-desktop-components.md) fournit des macros et des fonctions d’aide qui simplifient le développement de COM. Pour plus d’informations, voir [les composants de bureau ATL COM](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Applications de la plateforme Windows universelle

La plate-forme Windows universelle (UWP) est l’API Windows moderne. Les applications UWP s’exécutent sur n’importe quel appareil Windows 10, utilisent XAML pour l’interface utilisateur et sont entièrement tactiles. Pour plus d’informations sur UWP, voir [What’s a Universal Windows Platform (UWP) app?](/windows/uwp/get-started/whats-a-uwp) et [Guide to Windows Universal Apps](/windows/uwp/get-started/universal-application-platform-guide).

Le support original de CMD pour UWP se composait de (1) C/CX, un dialecte de C avec extensions de syntaxe, ou (2) la bibliothèque Windows Runtime (WRL), qui est basée sur la norme C et COM. Les deux C /CX et WRL sont toujours pris en charge. Pour les nouveaux projets, nous recommandons [C '/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), qui est entièrement basé sur la norme C 'et fournit des performances plus rapides.

## <a name="desktop-bridge"></a>Pont du bureau

Dans Windows 10, vous pouvez emballer votre application de bureau existante ou votre objet COM comme une application UWP, et ajouter des fonctionnalités UWP telles que le toucher ou appeler les API à partir de l’ensemble moderne d’API Windows. Vous pouvez également ajouter une application UWP à une solution de bureau dans Visual Studio, et les emballer ensemble dans un seul paquet et utiliser des API Windows pour communiquer entre eux.

Visual Studio 2017 version 15.4 et plus tard vous permet de créer un projet windows Application Package pour simplifier considérablement le travail d’emballage de votre application de bureau existante. Quelques restrictions s’appliquent aux appels de registre ou aux API que votre application de bureau peut utiliser. Cependant, dans de nombreux cas, vous pouvez créer d’autres voies de code pour atteindre des fonctionnalités similaires tout en exécutant dans un paquet d’applications. Pour plus d’informations, consultez [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Jeux

Les jeux DirectX peuvent s’exécuter sur PC ou Xbox. Pour plus d’informations, voir [DirectX Graphics and Gaming](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>Clients de la base de données SQL Server

Pour accéder aux bases de données SQL Server à partir de code natif, utilisez ODBC ou OLE DB. Pour plus d’informations, consultez [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Pilotes de périphérique Windows

Les pilotes sont des composants de bas niveau qui rendent les données des périphériques matériels accessibles aux applications et autres composants du système d’exploitation. Pour plus d’informations, voir [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Services Windows

Un *service* Windows est un programme qui peut s’exécuter en arrière-plan avec peu ou pas d’interaction utilisateur. Ces programmes sont appelés *daemons* sur les systèmes UNIX. Pour plus d’informations, voir [Services](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>SDKs, bibliothèques et fichiers d’en-tête

Visual Studio comprend la C Runtime Library (CRT), la Bibliothèque Standard C et d’autres bibliothèques spécifiques à Microsoft. La plupart des dossiers comprennent qui contiennent des fichiers d’en-tête pour ces bibliothèques sont situés dans le répertoire d’installation Visual Studio sous le dossier 'VC'. Les fichiers d’en-tête Windows et CRT se trouvent dans le dossier d’installation Windows SDK.

Le [gestionnaire de forfait Vcpkg](../build/vcpkg.md) vous permet d’installer facilement des centaines de bibliothèques open source tierces pour Windows.

Les bibliothèques Microsoft comprennent :

- Bibliothèque MFC (Microsoft Foundation Classes) : infrastructure orientée objet conçue pour la création de programmes Windows traditionnels (notamment des applications d’entreprise) qui possèdent des interfaces utilisateur riches dotées de boutons, de zones de liste, d’arborescences et d’autres contrôles. Pour plus d'informations, consultez [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Bibliothèque ATL (Active Template Library) : bibliothèque d'assistance puissante pour créer des composants COM. Pour plus d'informations, consultez [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism) : bibliothèque qui permet un travail de calcul général à hautes performances sur le GPU. Pour plus d'informations, consultez [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime d'accès concurrentiel : bibliothèque qui simplifie le travail de programmation parallèle et asynchrone pour les appareils dotés de plusieurs cœurs, voire de nombreux cœurs. Pour plus d'informations, consultez [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

De nombreux scénarios de programmation Windows requièrent également le Kit de développement logiciel Windows, qui inclut les fichiers d'en-tête qui permettent l'accès aux composants du système d'exploitation Windows. Par défaut, Visual Studio installe le Windows SDK comme composant de la charge de travail de CD Desktop, qui permet le développement d’applications Windows universelles. Pour développer des applications UWP, vous avez besoin de la version Windows 10 du SDK Windows. Pour plus d’informations, voir [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Pour plus d’informations sur les SDK Windows pour les versions antérieures de Windows, voir [l’archive Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Fichiers de programme (x86) - Windows Kits** est l’emplacement par défaut pour toutes les versions de la SDK Windows que vous avez installé.

D'autres plateformes, telles que Xbox et Azure, possèdent leurs propres Kits de développement logiciel que vous pouvez être amené à installer. Pour plus d'informations, consultez le Centre de développement DirectX et le Centre de développement Azure.

## <a name="development-tools"></a>Outils de développement

Visual Studio inclut un débogueur puissant pour le code natif, des outils d’analyse statique, des outils de débogage graphique, un éditeur de code complet, la prise en charge des tests unitaires et de nombreux autres outils et utilitaires. Pour plus d’informations, voir [Get started developing with Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), et Overview of C ' development in Visual [Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>Contenu de cette section

|Intitulé|Description|
|-----------|-----------------|
|[Procédure pas à pas : Création d’un programme standard de CMD](walkthrough-creating-a-standard-cpp-program-cpp.md)| Créez une application de console Windows.|
|[Procédure pas à pas : création d’applications de bureau Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Créez une application de bureau Windows native.|
|[Assistant Windows Desktop](windows-desktop-wizard.md)|Utilisez l’assistant pour créer de nouveaux projets Windows.|
|[Bibliothèque ATL (Active Template Library)](../atl/atl-com-desktop-components.md)|Utilisez la bibliothèque ATL pour créer des composants COM dans le C.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Utilisez MFC pour créer de grandes ou petites applications Windows avec des dialogues et des contrôles|
|[Cours partagés ATL et MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Utilisez des cours tels que CString qui sont partagés dans ATL et MFC.|
|[Accès aux données](../data/data-access-in-cpp.md)| OLE DB et ODBC|
|[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)|Différents types de chaînes sur Windows.|
|[Ressources pour créer un jeu à l’aide de DirectX](resources-for-creating-a-game-using-directx.md)
|[Procédure : utilisation du Kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Kit de développement logiciel (SDK) Windows|
|[Utilisation des fichiers de ressources](working-with-resource-files.md)|Comment ajouter des images, des icônes, des tables de chaîne et d’autres ressources à une application de bureau.|
|[Ressources pour la création d'un jeu à l'aide de DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Liens vers le contenu pour la création de jeux en C.|
|[Procédure : utilisation du Kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Contient les étapes pour configurer votre projet à générer avec le Kit de développement logiciel (SDK) Windows 10.|
|[Déploiement des applications de bureau natives](deploying-native-desktop-applications-visual-cpp.md)|Déployez des applications natives sur Windows.|

## <a name="related-articles"></a>Articles connexes

|Intitulé|Description|
|-----------|-----------------|
|[CMD en Studio Visuel](../overview/visual-cpp-in-visual-studio.md)|Sujet parent pour le contenu du développeur Visual CMD.|
[.NET Développement avec C '/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Créez des emballages pour les bibliothèques CMD natives qui lui permettent de communiquer avec des applications et des composants .NET.|
|[Extensions de composants pour .NET et UWP](../extensions/component-extensions-for-runtime-platforms.md)|Référence pour les éléments syntaxiques partagés par C'/CX et CMD/CLI.|
|[Applications de plateforme Windows universelle (C++)](../cppcx/universal-windows-apps-cpp.md)|Écrivez des applications UWP à l’aide de CMD/CX ou de Windows Runtime Template Library (WRL).|
|[Attributs C++ pour COM et .NET](attributes/cpp-attributes-com-net.md)|Attributs non standard pour la programmation Windows uniquement à l’aide de .NET ou COM.|
