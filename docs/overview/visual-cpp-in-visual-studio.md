---
title: C++ dans Visual Studio
description: Découvrez comment utiliser le compilateur Microsoft C/C++, l’éditeur de code et les outils associés dans Visual Studio pour développer des programmes pour Windows, Linux, Android et iOS.
ms.date: 11/05/2020
ms.technology: cpp-ide
helpviewer_keywords:
- Visual C++, home page
ms.openlocfilehash: 32d8f45c1ae0ffeabcfd7b22988f125b138c1f4d
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334154"
---
# <a name="c-in-visual-studio"></a>C++ dans Visual Studio

:::moniker range="msvc-160"

> [!NOTE]
> Cette documentation pour développeurs s’applique à Visual Studio 2019. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.
>
> Si vous recherchez un package redistribuable Microsoft Visual C++ 2019 pour pouvoir exécuter un programme, accédez à la page de [Téléchargement](https://visualstudio.microsoft.com/downloads/) de Microsoft Visual Studio site. Sous **tous les téléchargements** , développez la section **autres outils, infrastructures et redistribuables** . Sélectionnez votre architecture cible, puis cliquez sur le bouton **Télécharger** .
>
> Pour les fichiers redistribuables plus anciens, ouvrez la page [téléchargements plus anciens](https://visualstudio.microsoft.com/vs/older-downloads/) . Développez la section **autres outils, infrastructures et redistribuables** . Recherchez la version redistribuable que vous souhaitez télécharger, sélectionnez votre architecture cible, puis cliquez sur le bouton **Télécharger** .

:::moniker-end

:::moniker range="msvc-150"

> [!NOTE]
> Cette documentation pour développeurs s’applique à Visual Studio 2017. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.
>
> Si vous recherchez un package redistribuable Microsoft Visual C++ 2017 ou plus ancien pour pouvoir exécuter un programme, accédez à la page des [téléchargements les plus anciens](https://visualstudio.microsoft.com/vs/older-downloads/) du site Microsoft Visual Studio. Développez la section **autres outils, infrastructures et redistribuables** . Recherchez la version redistribuable que vous souhaitez télécharger, sélectionnez votre architecture cible, puis cliquez sur le bouton **Télécharger** .

:::moniker-end

:::moniker range="msvc-140"

> [!NOTE]
> Cette documentation pour développeurs s’applique à Visual Studio 2015. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.
>
> Si vous recherchez un package redistribuable Microsoft Visual C++ 2015 ou plus ancien pour pouvoir exécuter un programme, accédez à la page des [téléchargements les plus anciens](https://visualstudio.microsoft.com/vs/older-downloads/) du site Microsoft Visual Studio. Développez la section **autres outils, infrastructures et redistribuables** . Recherchez la version redistribuable que vous souhaitez télécharger, sélectionnez votre architecture cible, puis cliquez sur le bouton **Télécharger** .

:::moniker-end

Microsoft Visual C++ (MSVC) fait référence aux outils et bibliothèques de développement du langage C++, C et assembly disponibles dans le cadre de Visual Studio sur Windows. Ces outils et bibliothèques vous permettent de créer des applications de plateforme Windows universelle (UWP), des applications serveur et de bureau Windows natives, des bibliothèques multiplateformes et des applications qui s’exécutent sur Windows, Linux, Android et iOS, ainsi que des applications et des bibliothèques managées qui utilisent le .NET Framework. Vous pouvez utiliser MSVC pour écrire des applications de console simples vers les applications les plus sophistiquées et complexes pour Windows Desktop, depuis les pilotes de périphériques et les composants du système d’exploitation vers des jeux multiplateformes pour les appareils mobiles, et des appareils IoT les plus petits vers l’informatique multi-serveur à hautes performances dans le Cloud Azure.

Les versions de Visual Studio 2015, 2017 et 2019 peuvent être installées côte à côte. Vous pouvez utiliser Visual Studio 2019 (ensemble d’outils du compilateur V142) ou Visual Studio 2017 (V141) pour modifier et générer des programmes à l’aide de l’ensemble d’outils de Visual Studio 2017 (V141) et de Visual Studio 2015 (V140).

## <a name="whats-new-and-conformance-history"></a>Nouveautés et historique de la conformité

[Nouveautés de C++ dans Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)\
Découvrez les nouveautés de Visual Studio.

[Nouveautés de C++ dans Visual Studio 2003 à 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
Découvrez ce qui était nouveau dans C++ pour chaque version de Visual Studio de 2003 à 2015.

[Améliorations de la conformité de C++ dans Visual Studio](cpp-conformance-improvements.md)\
Découvrez les améliorations de la conformité de C++ dans Visual Studio.

[Table de conformité du langage Microsoft C++](visual-cpp-language-conformance.md)\
Liste des états de conformité par fonctionnalité dans le compilateur MSVC C++.

[Historique des modifications Microsoft C/C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
Découvrez les modifications avec rupture introduites dans cette version.

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>Installer Visual Studio et mettre à niveau à partir de versions antérieures

[Installer la prise en charge de C++ dans Visual Studio](../build/vscpp-step-0-installation.md)\
Téléchargez Visual Studio et installez l’ensemble d’outils Microsoft C/C++.

[Guide de Portage et de mise à niveau de Microsoft C++](../porting/visual-cpp-porting-and-upgrading-guide.md)\
Conseils sur le portage de code et la mise à niveau des projets vers Visual Studio 2015 ou ultérieur en vue de bénéficier de la meilleure conformité du compilateur à la norme C++, ainsi que de temps de compilation et de fonctionnalités de sécurité grandement améliorés, comme l’atténuation Spectre.

[Outils et fonctionnalités C++ dans les éditions de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)\
Découvrez les différentes éditions de Visual Studio.

[Plateformes prises en charge](supported-platforms-visual-cpp.md)\
Découvrez les plateformes prises en charge par le compilateur Microsoft C/C++.

## <a name="learn-c"></a>Apprendre C++

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)\
En savoir plus sur les techniques de programmation C++ basées sur C++11 et ultérieur qui vous permettent d’écrire rapidement du code sécurisé et d’éviter la plupart des pièges de la programmation de style C.

[C++ standard](https://isocpp.org/)\
Découvrez C++, obtenez une vue d’ensemble du langage C++ moderne et bénéficiez de liens vers des ouvrages, des articles, des entretiens et des événements.

[En savoir plus sur Visual Studio et créer votre premier projet C++](../build/vscpp-step-1-create.md)\
Commencez à apprendre à écrire du C++ dans Visual Studio.

[Exemples Visual Studio C++](visual-cpp-samples.md)\
Informations sur les exemples de code C++ fournis par Microsoft.

## <a name="c-development-tools"></a>Outils de développement C++

[Vue d’ensemble du développement C++ dans Visual Studio](overview-of-cpp-development.md)\
Comment utiliser l’IDE Visual Studio pour créer des projets, modifier du code, établir des liaisons à des bibliothèques, compiler, déboguer, créer des tests unitaires, effectuer une analyse statique, déployer et bien plus encore.

[Projets et systèmes de génération](../build/projects-and-build-systems-cpp.md)\
Guide pratique pour créer et configurer des projets Visual Studio C++, des projets CMake et d’autres types de projets avec des options de compilateur et d’éditeur de liens MSVC.

[Écriture et refactorisation du code C++](../ide/writing-and-refactoring-code-cpp.md)\
Comment utiliser les fonctionnalités de productivité dans l’éditeur C++ pour refactoriser, parcourir, comprendre et écrire du code.

[Débogage de code natif](/visualstudio/debugger/debugging-native-code)\
Utiliser le débogueur Visual Studio avec des projets C++.

[Vue d’ensemble de l’analyse du code C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)\
Utilisez des annotations SAL ou les vérificateurs C++ Core Guidelines pour effectuer une analyse statique.

[Écrire des tests unitaires pour C/C++ dans Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp)\
Créer des tests unitaires à l’aide du Framework de tests unitaires Microsoft pour C++, Google Test, Boost.Test ou CTest.

## <a name="write-applications-in-c"></a>Écrire des applications en C++

[Applications Windows universelles (C++)](../cppcx/universal-windows-apps-cpp.md)\
Recherchez des guides et du contenu de référence dans le Centre de développement Windows. Pour plus d’informations sur le développement d’applications UWP, consultez [Présentation de la plateforme Windows universelle](/windows/uwp/get-started/universal-application-platform-guide) et [Créer votre première application UWP en C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

[Applications de bureau (C++)](../windows/desktop-applications-visual-cpp.md)\
Découvrez comment créer des applications de bureau C++ natives traditionnelles pour Windows.

[Programmation .NET avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)\
Découvrez comment créer des DLL qui permettent une interopérabilité entre les programmes C++ et .NET natifs écrits dans des langages tels que C# ou Visual Basic.

[Programmation Linux](../linux/index.yml)\
Utilisez l’IDE de Visual Studio pour coder et déployer sur une machine Linux distante pour une compilation avec GCC.

[Créer des dll C/C++ dans Visual Studio](../build/dlls-in-visual-cpp.md)\
Découvrez comment utiliser Win32, ATL et MFC pour créer des DLL de bureau Windows, et obtenez des informations sur la façon de compiler et d’enregistrer votre DLL.

[Programmation parallèle](../parallel/parallel-programming-in-visual-cpp.md)\
Apprenez à utiliser la bibliothèque de modèles parallèles, C++ AMP, OpenMP et d’autres fonctionnalités associées au multithreading dans Windows.

[Meilleures pratiques de sécurité](../security/security-best-practices-for-cpp.md)\
Apprenez à protéger des applications contre un code malveillant et une utilisation non autorisée.

[Cloud et programmation Web](../cloud/cloud-and-web-programming-in-visual-cpp.md)\
En C++, vous disposez de plusieurs options de connexion web et cloud.

[Accès aux données](../data/data-access-in-cpp.md)\
Se connecter aux bases de données à l’aide d’ODBC et d’OLE DB.

[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)\
En savoir plus sur l’utilisation de différents formats et encodages de texte et de chaîne pour un développement local et international.

## <a name="languages-reference"></a>Informations de référence sur les langages

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)\
Guide de référence de l’implémentation Microsoft du langage de programmation C++.

[Référence du préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)\
Référence commune au préprocesseur du langage C et C++ partagé.

[Référence du langage C](../c-language/c-language-reference.md)\
Guide de référence de l’implémentation Microsoft du langage de programmation C.

[Intrinsèques du compilateur et langage assembleur](../intrinsics/compiler-intrinsics-and-assembly-language.md)\
Repères des intrinsèques du compilateur pris en charge ou implémentés par les compilateurs Microsoft C/C++ sur chaque plateforme.

## <a name="c-libraries-in-visual-studio"></a>Bibliothèques C++ dans Visual Studio

Les sections suivantes fournissent des informations sur les différentes bibliothèques C et C++ incluses dans Visual Studio.

[Référence de la bibliothèque Runtime C](../c-runtime-library/c-run-time-library-reference.md)\
Inclut des solutions alternatives optimisées en matière de sécurité pour les fonctions connues pour poser des problèmes de sécurité.

[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)\
Bibliothèque C++ standard.

[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)\
Prise en charge des composants et des applications COM.

[Bibliothèques MFC (Microsoft Foundation Class)](../mfc/mfc-desktop-applications.md)\
Prise en charge pour la création d’applications de bureau dotées d’interfaces utilisateur traditionnelles ou Office.

[Bibliothèque de modèles parallèles (PPL)](../parallel/concrt/parallel-patterns-library-ppl.md)\
Algorithmes asynchrones et parallèles qui s’exécutent sur le processeur.

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)\
Algorithmes massivement parallèles qui s’exécutent sur le GPU.

[Bibliothèque de modèles Windows Runtime (WRL)](../cppcx/wrl/windows-runtime-cpp-template-library-wrl.md)\
Applications et composants de plateforme Windows universelle (UWP).

[Programmation .NET avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)\
Programmation du Common Langage Runtime (CLR).

## <a name="third-party-open-source-c-libraries"></a>Bibliothèques C++ open source tierces

L’outil en ligne de commande **vcpkg** multiplateforme simplifie considérablement la découverte et l’installation de plus de 900 bibliothèques open source C++. Consultez [vcpkg : Gestionnaire de package C++ pour Windows](../build/vcpkg.md).

## <a name="feedback-and-community"></a>Commentaires et communauté

[Microsoft Docs Q&A](/answers/topics/c%2B%2B.html)\
Microsoft Docs héberge des forums pouvant faire l’objet d’une recherche de questions et de réponses. Ajoutez une `C++` balise à votre billet pour obtenir de l’aide à la communauté sur les problèmes liés à C++.

[Comment signaler un problème avec l’ensemble d’outils Microsoft C/C++](how-to-report-a-problem-with-the-visual-cpp-toolset.md)\
Découvrez comment créer des rapports d’erreurs efficaces sur l’ensemble d’outils Microsoft C/C++ (compilateur, éditeur de liens et autres outils) et comment soumettre votre rapport.

Blog de l' [équipe Microsoft C++](https://devblogs.microsoft.com/cppblog/)\
Obtenez plus d’informations sur les nouvelles fonctionnalités et les informations les plus récentes des développeurs des outils C++ dans Visual Studio.

[Communauté des développeurs Visual Studio C++](https://aka.ms/vsfeedback/browsecpp)\
Obtenir de l’aide, signaler des bogues et faire des suggestions pour C++ dans Visual Studio.
