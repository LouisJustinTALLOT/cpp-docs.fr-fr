---
title: Vue d'ensemble de la programmation Windows en C++
ms.date: 05/06/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 585fda614acce85e286e25b807d0fda57d03758b
ms.sourcegitcommit: af580f3a11b19d22288424eac7ceae1bc24ab312
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355566"
---
# <a name="overview-of-windows-programming-in-c"></a>Vue d'ensemble de la programmation Windows en C++

Il existe plusieurs grandes catégories d’applications Windows que vous pouvez créer avec C++. Chacun a son propre modèle de programmation et un ensemble de bibliothèques spécifiques à Windows, mais le C++ tierces et bibliothèque standard C++ bibliothèques peuvent être utilisées dans un d’eux.

## <a name="command-line-console-applications"></a>Applications de ligne de commande (console)

Applications de console C++ exécuter à partir de la ligne de commande dans une fenêtre de console et peuvent afficher la sortie de texte uniquement. Pour plus d’informations, consultez [Applications Console](console-applications-in-visual-cpp.md).

## <a name="native-desktop-client-applications"></a>Applications clientes de bureau natives

Un *application cliente de bureau native* est un C ou C++ fenêtrée application qui utilise natif d’origine [API C de Windows ou COM Component Object Model () API](/windows/desktop/apiindex/windows-api-list) pour accéder au système d’exploitation. Ces API sont eux-mêmes écrits principalement en C. Il existe plusieurs façons pour créer une application de bureau native : Vous pouvez programmer à l’aide de l’API Win32 directement, à l’aide d’une boucle de messages de style C qui traite les événements de système d’exploitation. Ou, vous pouvez programmer à l’aide de *Microsoft Foundation Classes* (MFC), un peu et orienté objet C++ bibliothèque qui encapsule Win32. Ni approche est considéré comme « moderne » par rapport à la plateforme Windows universelle (UWP), mais les deux sont toujours intégralement pris en charge et ont des millions de lignes de code qui s’exécute dans le monde aujourd'hui. Une application Win32 qui s’exécute dans une fenêtre exige que le développeur à utiliser explicitement des messages de Windows à l’intérieur d’une fonction de procédure de Windows. Malgré son nom, une application Win32 peut être compilée comme un (x86) 32 bits ou 64 bits (x64) binaire. Dans l’IDE de Visual Studio, les conditions x86 Win32 sont synonymes.

Pour bien démarrer avec C++ Windows traditionnelle de programmation, consultez [prise en main Win32 et C++](/windows/desktop/LearnWin32/learn-to-program-for-windows). Une fois que vous comprenez certains Win32, il sera plus facile d’en savoir plus sur [MFC Desktop Applications](../mfc/mfc-desktop-applications.md). Pour obtenir un exemple d’une application de bureau C++ traditionnel qui utilise des graphiques sophistiquées, consultez [Hilo : Développement d’Applications C++ pour Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ ou .NET ?

En générale, programmation .NET dans C# est moins complexe, moins sujette aux erreurs et possède une API orientée objet plus moderne que Win32 ou MFC. Dans la plupart des cas, ses performances ne sont plus adéquates. Windows Presentation Foundation (WPF) pour les graphiques riches fonctionnalités de .NET, et vous pouvez utiliser Win32 et l’API de Runtime Windows moderne. En règle générale, nous recommandons l’utilisation de C++ pour les applications de bureau lorsque vous avez besoin :

- contrôle précis sur l’utilisation de la mémoire
- l’économie de plus grande importance dans la consommation d’énergie
- utilisation du GPU pour le calcul général
- l’accès à DirectX
- utilisation élevée des bibliothèques C++ standard

Il est également possible de combiner la puissance et l’efficacité de C++ avec la programmation .NET. Vous pouvez créer une interface utilisateur dans C# et utilisez C / c++ / CLI pour activer votre application d’utiliser des bibliothèques C++ natives. Pour plus d’informations, consultez [programmation .NET avec C++ / c++ / CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Composants COM

Le [composant COM (Object Model)](/windows/desktop/com/the-component-object-model) est une spécification qui permet aux programmes écrits dans différents langages pour communiquer entre eux. De nombreux composants de Windows sont implémentées en tant qu’objets COM et suivent les règles COM standard pour la création d’objets, la découverte de l’interface et la destruction d’objets.  À l’aide des objets COM à partir d’applications de bureau C++ est relativement simple, écrivez votre propre objet COM est toutefois plus avancée. Le [bibliothèque ATL (Active Template)](../atl/atl-com-desktop-components.md) fournit des macros et fonctions d’assistance qui simplifient le développement de COM. Pour plus d’informations, consultez [composants de bureau COM ATL](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Applications de la plateforme Windows universelle

La plateforme universelle Windows (UWP) est l’API Windows moderne. Applications UWP s’exécuter sur n’importe quel appareil Windows 10, utilisent XAML pour l’interface utilisateur et sont entièrement tactile. Pour plus d’informations sur UWP, consultez [qu’est une application de plateforme universelle Windows (UWP) ?](/windows/uwp/get-started/whats-a-uwp) et [Guide des applications universelles Windows](/windows/uwp/get-started/universal-application-platform-guide).

La version d’origine C++ prise en charge de UWP est composé de (1) C++/CX, un dialecte de C++ avec les extensions de syntaxe, ou (2) la bibliothèque de Runtime de Windows (WRL), qui est basé sur standard C++ et COM. C++ / c++ / CX et WRL sont toujours pris en charge. Pour les nouveaux projets, nous vous recommandons de [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), qui est entièrement basé sur standard C++ et offre des performances supérieures.

## <a name="desktop-bridge"></a>Pont du bureau

Dans Windows 10, vous pouvez empaqueter votre application de bureau existante ou d’un objet COM en tant qu’une application UWP et ajouter des fonctionnalités telles que touch UWP ou appeler des API à partir de l’ensemble d’API de Windows moderne. Vous pouvez également ajouter une application UWP à une solution de postes de travail dans Visual Studio et utilisez-les dans un seul package et que vous utilisent les API de Windows pour communiquer entre eux de package.

Visual Studio 2017 version 15.4 et versions ultérieure vous permet de créer un projet de Package d’Application Windows pour simplifier considérablement le travail d’empaquetage de votre application de bureau existante. Quelques restrictions s’appliquent pour les appels de Registre ou les API de votre application de bureau peut utiliser. Toutefois, dans de nombreux cas, vous pouvez créer des chemins de code de remplacement pour obtenir une fonctionnalité similaire lors de l’exécution dans un package d’application. Pour plus d’informations, consultez [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Jeux

Jeux DirectX peuvent s’exécuter sur le PC ou Xbox. Pour plus d’informations, consultez [graphiques et jeux DirectX](/windows/desktop/directx).

## <a name="sql-server-database-clients"></a>Clients de base de données SQL Server

Pour accéder aux bases de données SQL Server à partir du code natif, utilisez ODBC ou OLE DB. Pour plus d’informations, consultez [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Pilotes de périphérique Windows

Les pilotes sont des composants de bas niveau qui rendent les données à partir de périphériques matériels accessible aux applications et d’autres composants de système d’exploitation. Pour plus d’informations, consultez [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Services Windows

Un Windows *service* est un programme qui peut s’exécuter en arrière-plan avec peu ou aucune intervention de l’utilisateur. Ces programmes sont appelés *démons* sur les systèmes UNIX. Pour plus d’informations, consultez [Services](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>SDK, bibliothèques et fichiers d’en-tête

Visual Studio inclut la bibliothèque Runtime C (CRT), la bibliothèque C++ Standard et autres bibliothèques spécifiques à Microsoft. La plupart des dossiers include qui contiennent les fichiers d’en-tête pour ces bibliothèques est située dans le répertoire d’installation de Visual Studio dans le dossier \VC\. Les fichiers d’en-tête Windows et de la bibliothèque CRT sont trouvent dans le dossier d’installation du SDK Windows.

Le [Gestionnaire de package Vcpkg](../build/vcpkg.md) vous permet d’installer facilement des centaines de bibliothèques de tiers open source pour Windows.

Les bibliothèques Microsoft incluent :

- Microsoft Foundation Classes (MFC) : Une infrastructure orientée objet pour la création de programmes Windows traditionnels, en particulier les applications d’entreprise, qui ont des interfaces utilisateur riches dotées de boutons, des zones de liste, des vues de l’arborescence et d’autres contrôles. Pour plus d'informations, consultez [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL) : Une bibliothèque d’assistance puissante pour la création de composants COM. Pour plus d'informations, consultez [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism) : Une bibliothèque qui permet le travail de calcul général hautes performances sur le GPU. Pour plus d'informations, consultez [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime d’accès concurrentiel : Une bibliothèque qui simplifie le travail de la programmation asynchrone et parallèle pour les appareils multicœurs et de nombreux cœurs. Pour plus d'informations, consultez [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

De nombreux scénarios de programmation Windows requièrent également le Kit de développement logiciel Windows, qui inclut les fichiers d'en-tête qui permettent l'accès aux composants du système d'exploitation Windows. Par défaut, Visual Studio installe le Kit de développement logiciel Windows en tant que composant de la charge de travail C++ Desktop, ce qui permet le développement d’applications de Windows Universal. Pour développer des applications UWP, vous avez besoin de la version de Windows 10 du Kit de développement Windows. Pour plus d’informations, consultez [SDK Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Pour plus d’informations sur les kits de développement logiciel Windows pour les versions antérieures de Windows, consultez le [archive du SDK Windows](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Programmer des fichiers (x86) \Windows Kits** est l’emplacement par défaut pour toutes les versions du SDK Windows que vous avez installées.

D'autres plateformes, telles que Xbox et Azure, possèdent leurs propres Kits de développement logiciel que vous pouvez être amené à installer. Pour plus d'informations, consultez le Centre de développement DirectX et le Centre de développement Azure.

## <a name="development-tools"></a>Outils de développement

Visual Studio inclut un débogueur puissant pour le code natif, des outils d’analyse statique, des outils de débogage graphique, un éditeur de code complet, la prise en charge des tests unitaires et de nombreux autres outils et utilitaires. Pour plus d’informations, consultez [commencer à développer avec Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), et [développement en vue d’ensemble de C++ dans Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>Dans cette section
|Titre|Description|
|-----------|-----------------|
|[Procédure pas à pas : Création d’un programme C++ standard](walkthrough-creating-a-standard-cpp-program-cpp.md)| Créez une application de console Windows.|
|[Procédure pas à pas : création d’applications de bureau Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Créer une application de bureau Windows native.|
|[Assistant Windows Desktop](windows-desktop-wizard.md)|Utilisez l’Assistant pour créer des projets de Windows.|
|[Bibliothèque ATL (Active Template Library)](../atl/atl-com-desktop-components.md)|Utilisez la bibliothèque ATL pour créer des composants COM en C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Utiliser MFC pour créer de petites ou grandes applications Windows avec les contrôles et les boîtes de dialogue|
|[Classes partagées ATL et  MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Utilisez les classes telles que CString qui sont partagées dans ATL et MFC.|
|[Accès aux données](../data/data-access-in-cpp.md)| OLE DB et ODBC|
|[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)|Différents types de chaînes sur Windows.|
|[Ressources pour la création d’un jeu à l’aide de DirectX](resources-for-creating-a-game-using-directx.md)
|[Guide pratique pour utiliser le kit SDK Windows 10 dans une application de bureau Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|SDK Windows|
|[Utilisation des fichiers de ressources](working-with-resource-files.md)|Comment ajouter des images, des icônes, des tables de chaînes et d’autres ressources pour une application de bureau.|
|[Ressources pour la création d’un jeu à l’aide de DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Liens vers du contenu pour la création de jeux en C++.|
|[Guide pratique pour utiliser le kit SDK Windows 10 dans une application de bureau Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Contient les étapes pour configurer votre projet à générer avec le Kit de développement logiciel (SDK) Windows 10.|
|[Déploiement des applications de bureau natives](deploying-native-desktop-applications-visual-cpp.md)|Déployer des applications natives sur Windows.|

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Rubrique parente pour le contenu destiné aux développeurs Visual C++.|
[Développement .NET avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Créer des wrappers pour les bibliothèques C++ natives qui permettent de communication avec les applications et composants .NET.|
|[Extensions de composants pour .NET et UWP](../extensions/component-extensions-for-runtime-platforms.md)|Référence pour les éléments de syntaxe partagés par C / c++ / CX et c++ / CLI.|
|[Applications de plateforme Windows universelle (C++)](universal-windows-apps-cpp.md)|Écrire des applications UWP à l’aide de C++ / c++ / CX ou la bibliothèque de modèles Windows Runtime (WRL).|
|[Attributs C++ pour COM et .NET](attributes/cpp-attributes-com-net.md)|Attributs non standards pour la programmation Windows uniquement à l’aide de .NET ou COM.|
