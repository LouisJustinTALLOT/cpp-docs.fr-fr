---
title: C++ dans Visual Studio
description: Visual C++ est le nom employé pour le compilateur Microsoft C++, l’éditeur de code et les outils associés dans l’IDE Visual Studio. Utilisez Visual C++ pour développer des programmes pour Windows, Linux, Android et iOS.
ms.date: 05/13/2019
ms.technology: cpp-ide
helpviewer_keywords:
- Visual C++, home page
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 2706d232dba2a7971edd8d84da2b1d1399ed6e25
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934148"
---
# <a name="c-in-visual-studio"></a>C++ dans Visual Studio

> [!NOTE]
> Cette documentation pour les développeurs s’applique à Visual Studio 2015 et versions ultérieures. Utilisez le sélecteur de version figurant dans le coin supérieur gauche de la page pour le faire correspondre à votre version de Visual Studio.
>
> Si vous recherchez un package redistribuable Visual C++ pour pouvoir exécuter un programme, accédez au [Centre de téléchargement Microsoft](http://www.microsoft.com/download/) et entrez **Visual C++** dans la zone de recherche.

Microsoft Visual C++, généralement abrégé en Visual C++ ou MSVC, est le nom qui désigne les outils de développement C++, C et en langage assembleur et les bibliothèques disponibles dans le cadre de Visual Studio sur Windows. Ces outils et bibliothèques vous permettent de créer des applications de plateforme Windows universelle (UWP), des applications serveur et de bureau Windows natives, des bibliothèques multiplateformes et des applications qui s’exécutent sur Windows, Linux, Android et iOS, ainsi que des applications et des bibliothèques managées qui utilisent le .NET Framework. Vous pouvez utiliser Visual C++ pour écrire aussi bien des applications de console simples que des applications plus sophistiquées et complexes pour le Bureau Windows,des pilotes de périphériques et des composants de système d’exploitation que des jeux multiplateformes pour appareils mobiles, des très petits appareils IoT que des dispositifs HPC multiserveurs dans le cloud Azure.

Les versions de Visual Studio 2015, 2017 et 2019 peuvent être installées côte à côte. Vous pouvez utiliser Visual Studio 2019 (version 142 de l’ensemble d’outils du compilateur) pour modifier et générer des programmes à l’aide de l’ensemble d’outils de Visual Studio 2015 (version 140) et Visual Studio 2017 (version 141).

## <a name="whats-new-and-conformance-history"></a>Nouveautés et historique de la conformité

[Nouveautés de C++ dans Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
Découvrez les nouveautés dans Visual Studio.

[Nouveautés de C++ de Visual Studio 2003 à 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
Découvrez ce qui était nouveau dans C++ pour chaque version de Visual Studio de 2003 à 2015.

[Améliorations de la conformité de C++ dans Visual Studio](cpp-conformance-improvements.md)<br/>
Découvrez les améliorations de la conformité de C++ dans Visual Studio.

[Conformité du langage Visual C++](visual-cpp-language-conformance.md)<br/>
Liste des états de conformité par fonctionnalité dans le compilateur MSVC C++.

[Historique des modifications de Visual C++ entre 2003 et 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
Découvrez les modifications avec rupture introduites dans cette version.

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>Installer Visual Studio et mettre à niveau à partir de versions antérieures

[Installer la prise en charge de C++ dans Visual Studio](../build/vscpp-step-0-installation.md)<br/>
Téléchargez Visual Studio 2015 ou Visual Studio 2017 et installez l’ensemble d’outils Visual C++.

[Guide du portage et de la mise à niveau de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)<br/>
Conseils pour le portage de code et la mise à niveau de projets vers Visual 2015 ou Visual Studio 2017, notamment le portage de code C++ vers Windows 10 et la plateforme universelle Windows.

[Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)<br/>
Découvrez les différentes éditions de Visual Studio.

[Plateformes prises en charge](supported-platforms-visual-cpp.md)<br/>
Découvrez quelles plateformes sont prises en charge.

## <a name="learn-c"></a>Apprendre C++

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
En savoir plus sur les techniques de programmation C++ basées sur C++11 et C++14 qui vous permettent d’écrire rapidement du code sécurisé et d’éviter la plupart des pièges de la programmation de style C.

[C++ standard](http://isocpp.org/)<br/>
Découvrez C++, obtenez une vue d’ensemble du langage C++ moderne et bénéficiez de liens vers des ouvrages, des articles, des entretiens et des événements.

[Découvrir Visual C++](../build/vscpp-step-1-create.md)<br/>
Commencez à vous familiariser avec le langage C++.

[Exemples Visual C++](visual-cpp-samples.md)<br/>
Informations sur les exemples.

## <a name="c-development-tools"></a>Outils de développement C++

[Présentation du développement C++ dans Visual Studio](overview-of-cpp-development.md)<br/>
Comment utiliser l’IDE Visual Studio pour créer des projets, modifier du code, établir des liaisons à des bibliothèques, compiler, déboguer, créer des tests unitaires, effectuer une analyse statique, déployer et bien plus encore.

[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)<br/>
Guide pratique pour créer et configurer des projets Visual Studio C++, des projets CMake et d’autres types de projets avec des options de compilateur et d’éditeur de liens MSVC.

[Écriture et refactorisation du code C++](../ide/writing-and-refactoring-code-cpp.md)<br/>
Guide pratique pour utiliser les fonctionnalités de productivité dans l’éditeur C++ pour refactoriser, parcourir et écrire du code.

[Débogage du code natif](/visualstudio/debugger/debugging-native-code)<br/>
Utiliser le débogueur Visual Studio avec des projets C++.

[Vue d’ensemble de l’analyse du code C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)<br/>
Utilisez des annotations SAL ou les vérificateurs C++ Core Guidelines pour effectuer une analyse statique.

[Écrire des tests unitaires pour C/C++ dans Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp)<br/>
Créer des tests unitaires à l’aide du Framework de tests unitaires Microsoft pour C++, Google Test, Boost.Test ou CTest.

## <a name="write-applications-in-c"></a>Écrire des applications en C++

[Applications universelles Windows](../windows/universal-windows-apps-cpp.md)<br/>
Recherchez des guides et du contenu de référence dans le Centre de développement Windows. Pour plus d’informations sur le développement d’applications UWP, consultez [Présentation de la plateforme Windows universelle](/windows/uwp/get-started/universal-application-platform-guide) et [Créer votre première application UWP en C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

[Applications de bureau (C++)](../windows/desktop-applications-visual-cpp.md)<br/>
Découvrez comment créer des applications de bureau C++ natives traditionnelles pour Windows.

[Programmation .NET avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
Découvrez comment créer des DLL qui permettent une interopérabilité entre les programmes C++ et .NET natifs écrits dans des langages tels que C# ou Visual Basic.

[Programmation Linux](../linux/index.md)<br/>
Utilisez l’IDE de Visual Studio pour coder et déployer sur une machine Linux distante pour une compilation avec GCC.

[Création de DLL C/C++ dans Visual Studio](../build/dlls-in-visual-cpp.md)<br/>
Découvrez comment utiliser Win32, ATL et MFC pour créer des DLL de bureau Windows, et obtenez des informations sur la façon de compiler et d’enregistrer votre DLL.

[Programmation parallèle](../parallel/parallel-programming-in-visual-cpp.md)<br/>
Apprenez à utiliser la bibliothèque de modèles parallèles, C++ AMP, OpenMP et d’autres fonctionnalités associées au multithreading dans Windows.

[Bonnes pratiques de sécurité](../security/security-best-practices-for-cpp.md)<br/>
Apprenez à protéger des applications contre un code malveillant et une utilisation non autorisée.

[Cloud et programmation Web](../cloud/cloud-and-web-programming-in-visual-cpp.md)<br/>
En C++, vous disposez de plusieurs options de connexion web et cloud.

[Accès aux données](../data/data-access-in-cpp.md)<br/>
Connectez-vous aux bases de données à l’aide d’ODBC et d’autres technologies d’accès de base de données.

[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)<br/>
En savoir plus sur l’utilisation de différents formats et encodages de texte et de chaîne pour un développement local et international.

## <a name="languages-reference"></a>Informations de référence sur les langages

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)

[Informations de référence sur le préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)

[Informations de référence sur le langage C](../c-language/c-language-reference.md)

[Fonctions intrinsèques du compilateur et langage assembleur](../intrinsics/compiler-intrinsics-and-assembly-language.md)

## <a name="c-libraries-in-visual-studio"></a>Bibliothèques C++ dans Visual Studio

Les sections suivantes fournissent des informations sur les différentes bibliothèques C et C++ incluses dans Visual Studio.

[Référence sur les bibliothèques Runtime C](../c-runtime-library/c-run-time-library-reference.md)<br/>
Inclut des solutions alternatives optimisées en matière de sécurité pour les fonctions connues pour poser des problèmes de sécurité.

[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
Bibliothèque C++ standard.

[Bibliothèque ATL (Active Template Library)](../atl/atl-com-desktop-components.md)<br/>
Prise en charge des composants et des applications COM.

[Bibliothèques MFC (Microsoft Foundation Class)](../mfc/mfc-desktop-applications.md)<br/>
Prise en charge pour la création d’applications de bureau dotées d’interfaces utilisateur traditionnelles ou Office.

[Bibliothèque de modèles parallèles (PPL)](../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Algorithmes asynchrones et parallèles qui s’exécutent sur le processeur.

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
Algorithmes massivement parallèles qui s’exécutent sur le GPU.

[Bibliothèque de modèles Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
Applications et composants de plateforme Windows universelle (UWP).

[Programmation .NET avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
Programmation du Common Langage Runtime (CLR).

## <a name="third-party-open-source-c-libraries"></a>Bibliothèques C++ open source tierces

L’outil en ligne de commande **vcpkg** multiplateforme simplifie considérablement la découverte et l’installation de plus de 900 bibliothèques open source C++. Consultez [vcpkg : Gestionnaire de package C++ pour Windows](../build/vcpkg.md).

## <a name="feedback-and-community"></a>Commentaires et communauté

[Guide pratique pour signaler un problème avec l’ensemble d’outils Visual C++](how-to-report-a-problem-with-the-visual-cpp-toolset.md)<br/>
Découvrez comment créer des rapports d’erreurs efficaces portant sur l’ensemble d’outils Visual C++ (compilateur, éditeur de liens et autres outils) et différentes manières de soumettre votre rapport.

[Blog de l’équipe C++](https://devblogs.microsoft.com/cppblog/) Microsoft<br/>
Obtenez plus d’informations sur les nouvelles fonctionnalités et les informations les plus récentes des développeurs des outils C++ dans Visual Studio.

[Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/)<br/>
Découvrez comment obtenir de l’aide, consigner des bogues et envoyer des suggestions pour Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage C](../c-language/c-language-reference.md)
- [Référence sur les bibliothèques Runtime C](../c-runtime-library/c-run-time-library-reference.md)
- [Fonctions intrinsèques du compilateur et langage assembleur](../intrinsics/compiler-intrinsics-and-assembly-language.md)
