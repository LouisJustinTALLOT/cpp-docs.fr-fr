---
title: Vue d'ensemble de la programmation Windows en C++
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: cd95332721f51ed2d17c3205cba5f1456a1037b9
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075487"
---
# <a name="overview-of-windows-programming-in-c"></a>Vue d'ensemble de la programmation Windows en C++

Il existe plusieurs grandes catégories d’applications Windows que vous pouvez créer avec C++. Chacun possède son propre modèle de programmation et un ensemble de bibliothèques spécifiques à Windows, C++ mais la bibliothèque standard et les C++ bibliothèques tierces peuvent être utilisées dans l’un d’eux.

Cette section explique comment utiliser Visual Studio et les bibliothèques wrappers MFC/ATL pour créer des programmes Windows. Pour obtenir de la documentation sur la plateforme Windows elle-même, consultez la [documentation Windows](/windows/index).

## <a name="command-line-console-applications"></a>Applications de ligne de commande (console)

C++les applications console s’exécutent à partir de la ligne de commande dans une fenêtre de console et peuvent afficher une sortie texte uniquement. Pour plus d’informations, consultez [créer C++ un projet d’application console](../get-started/tutorial-console-cpp.md).

## <a name="native-desktop-client-applications"></a>Applications clientes Native Desktop

Une *application cliente de bureau Native* est une C++ application c ou Window qui utilise les API Windows c natives d’origine [ou les API COM (Component Object Model)](/windows/win32/apiindex/windows-api-list) pour accéder au système d’exploitation. Ces API sont elles-mêmes écrites principalement en C. Il existe plusieurs façons de créer une application de bureau Native : vous pouvez programmer à l’aide des API Win32 directement, à l’aide d’une boucle de message de style C qui traite les événements du système d’exploitation. Ou vous pouvez programmer à l’aide de *Microsoft Foundation classes* (MFC), une bibliothèque orientée C++ objet légère qui encapsule Win32. Aucune approche n’est considérée comme « moderne » par rapport à la plateforme Windows universelle (UWP), mais les deux sont toujours entièrement prises en charge et ont des millions de lignes de code s’exécutant dans le monde aujourd’hui. Une application Win32 qui s’exécute dans une fenêtre exige que le développeur travaille explicitement avec des messages Windows dans une fonction de procédure Windows. Malgré le nom, une application Win32 peut être compilée en tant que binaire 32 bits (x86) ou 64 bits (x64). Dans l’IDE de Visual Studio, les termes x86 et Win32 sont synonymes.

Pour vous familiariser avec la C++ programmation Windows traditionnelle, consultez [prise en main C++de Win32 et ](/windows/win32/LearnWin32/learn-to-program-for-windows). Une fois que vous aurez appris à utiliser Win32, il sera plus facile d’en savoir plus sur les [applications de bureau MFC](../mfc/mfc-desktop-applications.md). Pour obtenir un exemple d’application C++ de bureau classique qui utilise des graphiques sophistiqués, consultez [Hilo : développement C++ d’applications pour Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ou .NET ?

En général, la programmation .NET C# dans est moins complexe, moins sujette aux erreurs et a une API orientée objet plus moderne que Win32 ou MFC. Dans la plupart des cas, ses performances sont plus que adéquates. .NET propose le Windows Presentation Foundation (WPF) pour les graphiques enrichis, et vous pouvez utiliser Win32 et l’API Windows Runtime moderne. En règle générale, nous vous recommandons d' C++ utiliser pour les applications de bureau lorsque vous avez besoin des éléments suivants :

- contrôle précis de l’utilisation de la mémoire
- la plus grande économie de la consommation d’énergie
- utilisation du GPU pour l’informatique générale
- accès à DirectX
- utilisation intensive de bibliothèques C++ standard

Il est également possible de combiner la puissance et l’efficacité C++ de la programmation .net. Vous pouvez créer une interface utilisateur dans C# et utiliser C++/CLI pour permettre à l’application de consommer C++ des bibliothèques natives. Pour plus d’informations, consultez [programmation .NET C++avec/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Composants COM

Le [modèle COM (Component Object Model)](/windows/win32/com/the-component-object-model) est une spécification qui permet aux programmes écrits dans différents langages de communiquer les uns avec les autres. De nombreux composants Windows sont implémentés en tant qu’objets COM et suivent des règles COM standard pour la création d’objets, la découverte d’interfaces et la destruction d’objets.  L’utilisation d’objets C++ com à partir d’applications de bureau est relativement simple, mais l’écriture de votre propre objet com est plus avancée. La [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) fournit des macros et des fonctions d’assistance qui simplifient le développement com. Pour plus d’informations, consultez [ATL com Desktop Components](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Applications de la plateforme Windows universelle

La plateforme Windows universelle (UWP) est l’API Windows moderne. Les applications UWP s’exécutent sur n’importe quel appareil Windows 10, utilisent XAML pour l’interface utilisateur et sont entièrement compatibles avec la technologie tactile. Pour plus d’informations sur UWP, consultez [qu’est-ce qu’une application plateforme Windows universelle (UWP)](/windows/uwp/get-started/whats-a-uwp) et [Guide pour les applications Windows universelles](/windows/uwp/get-started/universal-application-platform-guide).

La prise C++ en charge d’origine de UWP était de ( C++1)/CX, un C++ dialecte de avec des extensions de syntaxe, ou (2) la bibliothèque de Windows Runtime (WRL) C++ , qui est basée sur standard et com. C++/CX et WRL sont toujours pris en charge. Pour les nouveaux projets, nous vous recommandons [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), qui est entièrement basé C++ sur standard et qui offre des performances plus rapides.

## <a name="desktop-bridge"></a>Pont Desktop

Dans Windows 10, vous pouvez empaqueter votre application de bureau ou votre objet COM existant en tant qu’application UWP, et ajouter des fonctionnalités UWP telles que Touch ou appeler des API à partir du jeu d’API Windows moderne. Vous pouvez également ajouter une application UWP à une solution de bureau dans Visual Studio et les empaqueter dans un package unique et utiliser des API Windows pour communiquer entre elles.

Visual Studio 2017 version 15,4 et les versions ultérieures vous permettent de créer un projet de package d’application Windows pour simplifier de manière considérable le travail d’empaquetage de votre application de bureau existante. Certaines restrictions s’appliquent aux appels de registre ou aux API que votre application de bureau peut utiliser. Toutefois, dans de nombreux cas, vous pouvez créer d’autres chemins de code pour obtenir des fonctionnalités similaires lors de l’exécution dans un package d’application. Pour plus d’informations, consultez [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Jeux

Les jeux DirectX peuvent s’exécuter sur le PC ou la Xbox. Pour plus d’informations, consultez [graphiques et jeux DirectX](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>Clients de base de données SQL Server

Pour accéder aux bases de données SQL Server à partir du code natif, utilisez ODBC ou OLE DB. Pour plus d’informations, consultez [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Pilotes de périphérique Windows

Les pilotes sont des composants de bas niveau qui rendent les données des périphériques matériels accessibles aux applications et autres composants du système d’exploitation. Pour plus d’informations, consultez [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Services Windows

Un *service* Windows est un programme qui peut s’exécuter en arrière-plan avec peu ou pas d’intervention de l’utilisateur. Ces programmes sont appelés *démons* sur les systèmes UNIX. Pour plus d’informations, consultez [services](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>Kits de développement logiciel (SDK), bibliothèques et fichiers d’en-tête

Visual Studio comprend la bibliothèque Runtime C (CRT), la C++ bibliothèque standard et d’autres bibliothèques spécifiques à Microsoft. La plupart des dossiers include qui contiennent des fichiers d’en-tête pour ces bibliothèques se trouvent dans le répertoire d’installation de Visual Studio sous le dossier \VC\, soit Les fichiers d’en-tête Windows et CRT se trouvent dans le dossier d’installation de SDK Windows.

Le [Gestionnaire de package vcpkg](../build/vcpkg.md) vous permet d’installer facilement des centaines de bibliothèques Open source tierces pour Windows.

Les bibliothèques Microsoft incluent :

- Bibliothèque MFC (Microsoft Foundation Classes) : infrastructure orientée objet conçue pour la création de programmes Windows traditionnels (notamment des applications d’entreprise) qui possèdent des interfaces utilisateur riches dotées de boutons, de zones de liste, d’arborescences et d’autres contrôles. Pour plus d'informations, consultez [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Bibliothèque ATL (Active Template Library) : bibliothèque d'assistance puissante pour créer des composants COM. Pour plus d'informations, consultez [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism) : bibliothèque qui permet un travail de calcul général à hautes performances sur le GPU. Pour plus d'informations, consultez [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime d'accès concurrentiel : bibliothèque qui simplifie le travail de programmation parallèle et asynchrone pour les appareils dotés de plusieurs cœurs, voire de nombreux cœurs. Pour plus d’informations, consultez [Runtime d’accès concurrentiel](../parallel/concrt/concurrency-runtime.md).

De nombreux scénarios de programmation Windows requièrent également le Kit de développement logiciel Windows, qui inclut les fichiers d'en-tête qui permettent l'accès aux composants du système d'exploitation Windows. Par défaut, Visual Studio installe le SDK Windows en tant que composant de C++ la charge de travail de bureau, ce qui permet le développement d’applications Windows universelles. Pour développer des applications UWP, vous avez besoin de la version Windows 10 du SDK Windows. Pour plus d’informations, consultez [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Pour plus d’informations sur les kits de développement logiciel (SDK) Windows pour les versions antérieures de Windows, consultez l' [archive SDK Windows](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Program Files (x86) \Windows kits** est l’emplacement par défaut de toutes les versions du SDK Windows que vous avez installées.

D'autres plateformes, telles que Xbox et Azure, possèdent leurs propres Kits de développement logiciel que vous pouvez être amené à installer. Pour plus d'informations, consultez le Centre de développement DirectX et le Centre de développement Azure.

## <a name="development-tools"></a>Outils de développement

Visual Studio inclut un débogueur puissant pour le code natif, des outils d’analyse statique, des outils de débogage graphique, un éditeur de code complet, la prise en charge des tests unitaires et de nombreux autres outils et utilitaires. Pour plus d’informations, consultez la page prise en main du développement [avec Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)et [vue d’ensemble du C++ développement dans Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>Contenu de cette section
|Intitulé|Description|
|-----------|-----------------|
|[Procédure pas à pas : C++ création d’un programme standard](walkthrough-creating-a-standard-cpp-program-cpp.md)| Créez une application console Windows.|
|[Procédure pas à pas : création d’applications de bureau Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Créer une application de bureau Windows native.|
|[Assistant Windows Desktop](windows-desktop-wizard.md)|Utilisez l’Assistant pour créer des projets Windows.|
|[Bibliothèque ATL (Active Template Library)](../atl/atl-com-desktop-components.md)|Utilisez la bibliothèque ATL pour créer des composants COM C++dans.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Utiliser MFC pour créer des applications Windows volumineuses ou de petite taille avec des boîtes de dialogue et des contrôles|
|[Classes partagées ATL et  MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Utilisez des classes telles que CString, qui sont partagées dans ATL et MFC.|
|[Accès aux données](../data/data-access-in-cpp.md)| OLE DB et ODBC|
|[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)|Différents types de chaînes sur Windows.|
|[Ressources pour la création d’un jeu à l’aide de DirectX](resources-for-creating-a-game-using-directx.md)
|[Procédure : utilisation du kit SDK Windows 10 dans une application de bureau Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Kit de développement logiciel (SDK) Windows|
|[Utilisation des fichiers de ressources](working-with-resource-files.md)|Comment ajouter des images, des icônes, des tables de chaînes et d’autres ressources à une application de bureau.|
|[Ressources pour la création d’un jeu àC++l’aide de DirectX ()](resources-for-creating-a-game-using-directx.md)|Liens vers du contenu pour la création C++de jeux dans.|
|[Procédure : utilisation du kit SDK Windows 10 dans une application de bureau Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Contient les étapes pour configurer votre projet à générer avec le Kit de développement logiciel (SDK) Windows 10.|
|[Déploiement des applications de bureau natives](deploying-native-desktop-applications-visual-cpp.md)|Déployez des applications natives sur Windows.|

## <a name="related-articles"></a>Articles connexes

|Intitulé|Description|
|-----------|-----------------|
|[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Rubrique parente pour C++ le contenu du développeur Visual.|
[Développement .NET avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Créer des wrappers pour C++ les bibliothèques natives qui lui permettent de communiquer avec les applications et composants .net.|
|[Extensions de composants pour .NET et UWP](../extensions/component-extensions-for-runtime-platforms.md)|Référence pour les éléments de syntaxe C++partagés par C++/CX et/CLI.|
|[Applications de plateforme Windows universelle (C++)](../cppcx/universal-windows-apps-cpp.md)|Écrire des applications UWP C++à l’aide de/CX ou de la bibliothèque de modèles Windows Runtime (WRL).|
|[Attributs C++ pour COM et .NET](attributes/cpp-attributes-com-net.md)|Attributs non standard pour la programmation Windows uniquement à l’aide de .NET ou COM.|
