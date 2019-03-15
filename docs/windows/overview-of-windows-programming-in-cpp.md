---
title: Vue d'ensemble de la programmation Windows en C++
ms.date: 11/15/2018
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 6338b390b11c58f3ebac2af1bb568ea3c3470cd1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810443"
---
# <a name="overview-of-windows-programming-in-c"></a>Vue d'ensemble de la programmation Windows en C++

Il existe plusieurs grandes catégories d’applications Windows que vous pouvez créer avec C++. Chacun possède son propre modèle de programmation et ensemble de bibliothèques spécifiques de Windows, mais la bibliothèque standard C++, ainsi que les bibliothèques C++ de fournisseurs tiers peuvent être utilisés dans un d’eux. 

## <a name="command-line-console-applications"></a>Applications de ligne de commande (console)

Applications de console C++ exécuter à partir de la ligne de commande dans une fenêtre de console et peuvent afficher la sortie de texte uniquement. Pour plus d’informations, consultez [Applications Console](console-applications-in-visual-cpp.md).
 
## <a name="native-desktop-client-applications"></a>Applications clientes de bureau natives

Le terme *application de client de bureau native* fait référence à une application avec fenêtres C ou C++ qui utilise les API Win32 de Windows à l’adresse d’origine pour accéder au système d’exploitation. Ces API sont eux-mêmes écrits principalement en C. Lorsque vous créez ce type d’application, vous avez le choix de programmer directement sur une boucle de messages de style C qui traite les événements de système d’exploitation, ou à l’aide de *Microsoft Foundation Classes* (MFC), une bibliothèque C++ qui encapsule Win32 d’une manière qui est un peu et orienté objet. Aucune de ces approches est considéré comme « modern » par rapport à la plateforme Windows universelle (voir ci-dessous), mais les deux sont toujours totalement pris en charge et ont des millions de lignes de code qui s’exécute dans le monde aujourd'hui.

Pour bien démarrer avec C++ Windows traditionnelle de programmation, consultez [prise en main Win32 et C++](/windows/desktop/LearnWin32/learn-to-program-for-windows). Une fois que vous comprenez certains Win32, il sera plus facile d’en savoir plus sur [MFC Desktop Applications](/mfc/mfc-desktop-applications). Pour obtenir un exemple d’une application de bureau C++ traditionnel qui utilise des graphiques sophistiquées, consultez [Hilo : Développement d’Applications C++ pour Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ ou .NET ? 

Pour la plupart des scénarios d’application (en d’autres termes, pas ciblage UWP), envisagez d’utiliser C# et .NET. Il s’agit, car la programmation .NET est généralement moins complexe, moins sujette aux erreurs et possède une API orientée objet plus moderne que Win32 ou MFC. Dans la plupart des cas, ses performances ne sont plus adéquates. Windows Presentation Foundation (WPF) pour les graphiques riches fonctionnalités de .NET, et vous pouvez utiliser Win32, ainsi que le Windows modernes API Runtime (voir UWP ci-dessous). En règle générale, nous recommandons l’utilisation de C++ pour les applications de bureau lorsque vous avez besoin :

- contrôle précis sur l’utilisation de la mémoire
- l’économie de plus grande importance dans la consommation d’énergie
- utilisation du GPU pour le calcul général
- l’accès à DirectX
- utilisation élevée des bibliothèques C++ standard

## <a name="com-components"></a>Composants COM

Plusieurs parties du système d’exploitation Windows sont basés sur le composant COM (Object Model) qui définit une norme binaire qui permet au composant à être consommés à partir d’applications clientes écrites dans n’importe quel langage de l’ordinateur. En C++, vous pouvez utiliser la bibliothèque ATL (Active Template) pour simplifier le travail de création de vos propres composants COM. Pour plus d’informations, consultez [composant COM (Object Model)](/windows/desktop/com/component-object-model--com--portal) et [composants de bureau COM ATL](../atl/atl-com-desktop-components.md).

## <a name="windows-universal-apps"></a>Applications Windows universelles

La plateforme universelle Windows (UWP) est l’API Windows moderne. Applications UWP s’exécuter sur n’importe quel appareil Windows 10, utilisent XAML pour l’interface utilisateur et sont entièrement tactile. Pour plus d’informations sur UWP, consultez [qu’est une application de plateforme universelle Windows (UWP) ?](/windows/uwp/get-started/whats-a-uwp) et [Guide des applications universelles Windows](/windows/uwp/get-started/universal-application-platform-guide).

La prise en charge C++ d’origine pour UWP est composé de (1) C + c++ / CX, un dialecte de C++ avec des extensions de syntaxe, ou (2) la bibliothèque de Runtime Windows (WRL) qui est basée sur le standard C++ et COM. C++ / c++ / CX et WRL sont toujours pris en charge. Pour les nouveaux projets, nous recommandons [C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) qui est entièrement basé sur le langage C++ standard et offre des performances supérieures. 

Pour Windows 10, vous pouvez empaqueter votre application de bureau C++ existante en tant que-est pour le déploiement via le Microsoft Store. Pour plus d’informations, consultez [empaqueter des applications de bureau (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Jeux

Jeux DirectX peuvent s’exécuter sur le PC ou Xbox. Pour plus d’informations, consultez [graphiques et jeux DirectX](/windows/desktop/directx).

## <a name="net-wrappers-for-c-libraries"></a>Wrappers .NET pour les bibliothèques C++

Vous pouvez utiliser C++ / c++ / CLI pour créer une couche d’interopérabilité qui permet au code .NET consommer des bibliothèques C++ natives. Pour plus d’informations, consultez [programmation .NET avec C++ / c++ / CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="sql-server-database-clients"></a>Clients de base de données SQL Server

Pour accéder aux bases de données SQL Server à partir du code natif, utilisez ODBC ou OLE DB. Pour plus d’informations, consultez [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Pilotes de périphérique Windows

Les pilotes sont des composants de bas niveau qui rendent les données à partir de périphériques matériels accessible aux applications et d’autres composants de système d’exploitation. Pour plus d’informations, consultez [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Services Windows

Un Windows *service* est un programme qui peut s’exécuter en arrière-plan avec peu ou aucune intervention de l’utilisateur. Dans UNIX, ils sont appelés *démons*. Pour plus d’informations, consultez [Services](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>SDK, bibliothèques et fichiers d’en-tête

Visual Studio inclut la bibliothèque Runtime C (CRT), la bibliothèque C++ Standard et autres bibliothèques spécifiques à Microsoft. Les dossiers include qui contiennent les fichiers d’en-tête pour ces bibliothèques se trouvent dans le répertoire d’installation de Visual Studio dans le dossier \VC\, ou dans le cas de la bibliothèque CRT, dans le dossier d’installation du SDK Windows.

Vous pouvez utiliser la [Gestionnaire de package Vcpkg](../vcpkg.md) pour installer facilement des centaines de bibliothèques de tiers open source pour Windows.

Les bibliothèques Microsoft incluent :

- Microsoft Foundation Classes (MFC) : Une infrastructure orientée objet pour la création de programmes Windows traditionnels, en particulier les applications d’entreprise, qui ont des interfaces utilisateur riches dotées de boutons, des zones de liste, des vues de l’arborescence et d’autres contrôles. Pour plus d'informations, consultez [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL) : Une bibliothèque d’assistance puissante pour la création de composants COM. Pour plus d'informations, consultez [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism) : Une bibliothèque qui permet le travail de calcul général hautes performances sur le GPU. Pour plus d'informations, consultez [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Runtime d’accès concurrentiel : Une bibliothèque qui simplifie le travail de la programmation asynchrone et parallèle pour les appareils multicœurs et de nombreux cœurs. Pour plus d'informations, consultez [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

De nombreux scénarios de programmation Windows requièrent également le Kit de développement logiciel Windows, qui inclut les fichiers d'en-tête qui permettent l'accès aux composants du système d'exploitation Windows. Par défaut, Visual Studio installe le Kit de développement logiciel Windows en tant que composant de la charge de travail C++ Desktop, ce qui permet le développement d’applications de Windows Universal. Pour développer des applications UWP, vous avez besoin de la version de Windows 10 du Kit de développement Windows. Pour plus d’informations, consultez [SDK Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Pour plus d’informations sur les kits de développement logiciel Windows pour les versions antérieures de Windows, consultez le [archive du SDK Windows](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Programmer des fichiers (x86) \Windows Kits** est l’emplacement par défaut pour toutes les versions du SDK Windows que vous avez installée.

D'autres plateformes, telles que Xbox et Azure, possèdent leurs propres Kits de développement logiciel que vous pouvez être amené à installer. Pour plus d'informations, consultez le Centre de développement DirectX et le Centre de développement Azure.

## <a name="development-tools"></a>Outils de développement

Visual Studio inclut un débogueur puissant pour le code natif, des outils d’analyse statique, des outils de débogage graphique, un éditeur de code complet, la prise en charge des tests unitaires et de nombreux autres outils et utilitaires. Pour plus d’informations, consultez [commencer à développer avec Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), et [développement en vue d’ensemble de C++ dans Visual Studio](../overview-of-cpp-development.md).

## <a name="in-this-section"></a>Dans cette section
|Titre|Description|
|-----------|-----------------|
|[Applications de bureau Windows en C++](desktop-applications-visual-cpp.md)| Comment créer des applications de bureau traditionnelles.|
|[Bibliothèque ATL (Active Template Library)](../atl/TOC.md)|Utilisez la bibliothèque ATL pour créer des composants COM en C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/TOC.md)|Utiliser MFC pour créer de petites ou grandes applications Windows avec les contrôles et les boîtes de dialogue|
|[Classes partagées ATL et  MFC](../atl-mfc-shared/TOC.md)|Utilisez les classes telles que CString qui sont partagées dans ATL et MFC.|
|[Développement .NET avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Créer des wrappers pour les bibliothèques C++ natives qui permettent de communication avec les applications et composants .NET.|
|[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)|Référence pour les éléments de syntaxe partagés par C / c++ / CX et c++ / CLI.|
|[Applications de plateforme Windows universelle (C++)](universal-windows-apps-cpp.md)|Écrire des applications UWP à l’aide de C++ / c++ / CX ou la bibliothèque de modèles Windows Runtime (WRL).|
|[Attributs C++ pour COM et .NET](attributes/cpp-attributes-com-net.md)|Attributs non standards pour la programmation Windows uniquement à l’aide de .NET ou COM.|

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Rubrique parente pour le contenu destiné aux développeurs Visual C++.|
