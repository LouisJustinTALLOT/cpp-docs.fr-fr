---
description: 'En savoir plus sur : outils et fonctionnalités C++ dans les éditions de Visual Studio'
title: Outils et fonctionnalités C++ dans les éditions de Visual Studio
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 6253e52fa300cc60de4b2700b384fde6f5ffe1ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254623"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Outils et fonctionnalités C++ dans les éditions de Visual Studio

::: moniker range=">=msvc-160"

Les fonctionnalités C++ suivantes sont disponibles dans Visual Studio 2019. Sauf indication contraire, toutes les fonctionnalités sont disponibles dans toutes les éditions : Communauté Visual Studio, Visual Studio Professional et Visual Studio Enterprise. Certaines fonctionnalités nécessitent des charges de travail ou des composants facultatifs spécifiques que vous pouvez installer avec Visual Studio Installer.

## <a name="platforms"></a>Plateformes

- Bureau Windows
- Plateforme Windows universelle ((téléphone, tablette, PC, Xbox, IoT et HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>Compilateurs

- Compilateur MSVC 32 bits pour x86, x64, ARM et ARM64
- Compilateur MSVC 64 bits pour x86, x64, ARM et ARM64
- Compilateur croisé GCC pour ARM
- Clang/LLVM
  - Sur Windows, Clang/LLVM 7.0, ciblant x86 ou x64 (prise en charge de CMake uniquement). D’autres versions Clang peuvent fonctionner, mais ne sont pas officiellement prises en charge.
  - Sur Linux, toutes les installations Clang/LLVM prises en charge par le distributeur.

## <a name="c-workloads"></a>Charges de travail C++

Visual Studio comprend les charges de travail suivantes pour le développement C++. Vous pouvez les installer toutes ou une partie, ainsi que d’autres charges de travail telles que Développement .NET Desktop, Développement Python, Développement Azure, Développement d’extension Visual Studio et autres.

### <a name="desktop-development-with-c"></a>Développement Desktop en C++

Inclus :

- Fonctionnalités de bureau de base C++

Composants facultatifs :

- MSVC v142 - VS 2019 C++ x64/x86 build tools (v14.21)
- SDK Windows 10 (10.0.17763.0)
- Débogueur juste-à-temps
- Outils de profilage C++
- Outils C++ CMake pour Windows
- C++ ATL pour Build Tools v142 (x86 et x64)
- Adaptateur de test pour Boost.Test
- Adaptateur de test pour Google Test
- Live Share
- IntelliCode
- IntelliTrace (Enterprise uniquement)
- C++ MFC pour Build Tools v142 (x86 et x64)
- Prise en charge de C++/CLI pour Build Tools v142 (14.21)
- Modules C++ pour Build Tools v142 (x64/x86 – expérimental)
- Compilateur Clang pour Windows
- IncrediBuild - Accélération de build
- SDK Windows 10 (10.0.17134.0)
- SDK Windows 10 (10.0.16299.0)
- MSVC v141 - VS 2017 C++ x64/x86 Build Tools (v14.16)
- MSVC v140 – VS 2015 C++ Build Tools (v14.00)

### <a name="linux-development-with-c"></a>Développement Linux avec C++

Inclus :

- Fonctionnalités C++ de base
- Runtime C Windows universel
- Développement C++ pour Linux

Composants facultatifs :

- Outils C++ CMake pour Linux
- Outils de développement incorporé et IoT

### <a name="universal-windows-platform-development"></a>Développement pour la plateforme Windows universelle

Inclus :

- Blend pour Visual Studio
- .NET Native et .NET Standard
- Gestionnaire de package NuGet
- Outils de plateforme Windows universelle
- SDK Windows 10 (10.0.17763.0)

Composants facultatifs :

- IntelliCode
- IntelliTrace (Enterprise uniquement)
- Connectivité des périphériques USB
- Outils de plateforme Windows universelle C++ (v142)
- Outils de plateforme Windows universelle C++ (v141)
- Débogueur graphique et profileur GPU pour DirectX
- SDK Windows 10 (10.0.18362.0)
- SDK Windows 10 (10.0.17134.0)
- SDK Windows 10 (10.0.16299.0)
- Outils d’analyse et d’architecture

### <a name="c-game-development"></a>Développement de jeux C++

Inclus :

- Fonctionnalités C++ de base
- Runtime C Windows universel
- Mise à jour de Redistributable C++ 2019
- MSVC v142 - VS 2019 C++ x64/x86 build tools (v14.21)

Composants facultatifs :

- Outils de profilage C++
- SDK Windows 10 (10.0.17763.0)
- IntelliCode
- IntelliTrace (Enterprise uniquement)
- SDK Windows 10 (10.0.17134.0)
- SDK Windows 10 (10.0.16299.0)
- IncrediBuild - Accélération de build
- Cocos
- Programme d’installation Unreal Engine
- Prise en charge de l’IDE Android pour Unreal Engine

### <a name="mobile-development-with-c"></a>Développement mobile avec C++

Inclus :

- Fonctionnalités C++ de base
- Installation du kit Android SDK (niveau d’API 25) (installation locale pour le développement mobile en C++)

Composants facultatifs :

- Kit Android NDK (R16B)
- Apache Ant (1.9.3)
- Outils de développement C++ Android
- IntelliCode
- Émulateur Android Google (niveau d’API 25) (installation locale)
- Intel Hardware Accelerated Execution Manager (HAXM) (installation locale)
- Kit Android NDK (R16B) (32 bits)
- Outils de développement C++ iOS
- IncrediBuild - Accélération de build

## <a name="individual-components"></a>Composants individuels

Vous pouvez installer ces composants indépendamment de toute charge de travail.

- Diagnostics JavaScript
- Live Share
- Runtime de la plateforme Windows universelle en C++ pour Build Tools v142
- Publication ClickOnce
- Projets Microsoft Visual Studio Installer

## <a name="libraries-and-headers"></a>Bibliothèques et en-têtes

- En-têtes et bibliothèques Windows
- Windows Universal C Runtime (CRT)
- Bibliothèque standard C++
- ATL
- MFC
- Bibliothèque de classes .NET Framework
- Bibliothèque de prise en charge C++ pour .NET
- OpenMP 2.0
- Plus de 900 bibliothèques open source via le catalogue vcpkg

## <a name="build-and-project-systems"></a>Systèmes de génération et de projet

- CMake
- Tout système de build via Ouvrir un dossier
- Générations en mode ligne de commande (msbuild.exe)
- Multi-ciblage natif
- Multi-ciblage managé
- Générations en parallèle
- Personnalisations de la build
- Extensibilité des pages de propriétés

## <a name="project-templates"></a>Modèles de projet

Les modèles de projet suivants sont disponibles selon les charges de travail sur lesquelles vous avez effectué l’installation.

Bureau Windows :

- Projet vide
- Application console
- Assistant Windows Desktop
- Application de bureau Windows
- Projet d’éléments partagés
- Application MFC
- Bibliothèque de liens dynamiques
- Projet vide CLR
- Application de console CLR
- Bibliothèque statique
- Projet CMake
- Projet ATL
- Bibliothèque de liens dynamiques MFC
- Bibliothèque de classes CLR
- Projet Makefile (Windows)
- Contrôle ActiveX MFC
- Projet de test unitaire natif
- Google Test

Plateforme Windows universelle (C++/CX) :

- Application vide
- Application DirectX 11 et XAML
- DirectX 11 App
- Application DirectX 12
- Application de tests unitaires
- DLL
- Composant Windows Runtime
- Bibliothèque statique
- Projet de création de package d’application Windows

Linux :

- Application console (Linux)
- Projet vide (Linux)
- Raspberry Pi Blink
- Projet Makefile (Linux)

## <a name="tools"></a>Outils

- Éditeur de liens incrémentiel (Link.exe)
- Microsoft Makefile Utility (Nmake.exe)
- Générateur Lib (Lib.exe)
- Compilateur de ressources Windows (Rc.exe)
- Windows Resource to Object Converter (CvtRes.exe)
- Browse Information Maintenance Utility (BscMake.exe)
- C++ Name Undecorator (Undname.exe)
- COFF/PE Dumper (Dumpbin.exe)
- COFF/PE Editor (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- Règles d'inférence
- Optimisations guidées par profil

## <a name="debugging-features"></a>Fonctionnalités de débogage

- Débogage natif
- natvis (visualisation de type natif)
- Débogage graphique
- Débogage managé
- Utilisation du GPU
- Utilisation de la mémoire
- Remote Debugging
- Débogage SQL
- Analyse statique du code

## <a name="designers-and-editors"></a>Concepteurs et éditeurs

- Concepteur XAML
- Concepteur/éditeur de style CSS
- Concepteur/éditeur HTML
- Éditeur XML
- Éditeur de code source
- Fonctionnalités de productivité : refactorisation, moteur IntelliSense EDG, mise en forme du code C++
- Concepteur Windows Forms
- Concepteur de données
- Éditeur de ressources natives (fichiers .rc)
- Éditeurs de ressources
- Éditeur de modèle
- Concepteur Shader
- Validation de dépendances dynamique (Enterprise uniquement)
- Diagrammes de couches architecturales (Enterprise uniquement)
- Validation de l’architecture (Enterprise uniquement)
- Clone de code (Enterprise uniquement)

## <a name="data-features"></a>Fonctionnalités de données

- Concepteur de données
- Objets de données
- Services Web
- Explorateur de serveurs

## <a name="automation-and-extensibility"></a>Automatisation et extensibilité

- Modèles objet d'extensibilité
- Modèle de code
- Modèle de projet
- Modèle d'éditeur de ressources
- Modèle d'Assistant
- Modèle objet débogueur

## <a name="application-lifecycle-management-tools"></a>Outils de gestion du cycle de vie des applications

- Tests unitaires (Microsoft Native C++, Boost.Test, Google Test, CTest)
- Carte de code et graphes des dépendances (Professional et Enterprise)
- Couverture du code (Enterprise uniquement)
- Tests manuels (Enterprise uniquement)
- Tests exploratoires (Enterprise uniquement)
- Gestion de cas de test (Enterprise uniquement)
- Intégration du débogueur de la carte du code (Enterprise uniquement)
- Live Unit Testing (Enterprise uniquement)
- IntelliTrace (Enterprise uniquement)
- IntelliTest (Enterprise uniquement)
- Microsoft Fakes (isolement de tests unitaires) (Enterprise uniquement)
- Couverture du code (Enterprise uniquement)

## <a name="see-also"></a>Voir aussi

[Installer Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Nouveautés de Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Types de projets C++ dans Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=msvc-150"

Les tableaux suivants présentent les fonctionnalités Visual C++ disponibles dans Visual Studio 2017. La présence d’une croix (« X ») dans une cellule indique que la fonctionnalité est disponible ; une cellule vide indique que la fonctionnalité n’est pas disponible. Les remarques entre parenthèses indiquent qu'une fonctionnalité est disponible, mais limitée.

## <a name="platforms"></a>Plateformes

|Plateforme|Visual Studio Express pour Windows 10|Visual Studio Express pour Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|-|-|-|-|-|
|Bureau Windows||X|X|X|
|Plateforme Windows universelle ((téléphone, tablette, PC, Xbox, IoT et HoloLens))|X||X|X|
|Linux|X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Compilateurs

|Compilateur|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Compilateur MSVC 32 bits X86|X|X|X|X|
|Compilateur croisé X86_arm|X||X|X|
|Compilateur MSVC 64 bits x64|||X|X|
|Compilateur croisé X86_ x64|X|X|X|X|

## <a name="libraries-and-headers"></a>Bibliothèques et en-têtes

|Bibliothèque ou en-tête|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|En-têtes et bibliothèques Windows et bibliothèque CRT|(X)|X|X|X|
|Bibliothèque standard C++|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|Bibliothèque de classes .NET Framework||X|X|X|
|Bibliothèque de prise en charge C++ pour .NET||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>Modèles de projet

|Modèle|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Modèles XAML pour UWP, Windows 8.1, Windows Phone 8.0|X||X|X|
|Applications Direct3D|X||X|X|
|DLL (Windows universel)|X||X|X|
|Bibliothèque statique (Universal Windows)|X||X|X|
|Composant Windows Runtime|X||X|X|
|Application de test unitaire (Windows universel)|X||X|X|
|Projet ATL|||X|X|
|Bibliothèque de classes (CLR)||X|X|X|
|Application console CLR||X|X|X|
|Projet vide CLR||X|X|X|
|Assistant personnalisé|||X|X|
|Projet vide||X|X|X|
|Projet Makefile||X|X|X|
|Contrôle ActiveX MFC|||X|X|
|Application MFC|||X|X|
|DLL MFC|||X|X|
|Projet de test|X|X|X|X|
|Application console Win32||X|X|X|
|Projet Win32||X|X|X|

## <a name="tools"></a>Outils

|Outil|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Éditeur de liens incrémentiel (Link.exe)|X|X|X|X|
|Utilitaire de maintenance de programmes (Nmake.exe)||X|X|X|
|Générateur Lib (Lib.exe)|X|X|X|X|
|Compilateur de ressources Windows (Rc.exe)|X|X|X|X|
|Windows Resource to Object Converter (CvtRes.exe)||X|X|X|
|Browse Information Maintenance Utility (BscMake.exe)|X|X|X|X|
|C++ Name Undecorator (Undname.exe)|X|X|X|X|
|COFF/PE Dumper (Dumpbin.exe)|X|X|X|X|
|COFF/PE Editor (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|Règles d'inférence|||X|X|
|Mise à niveau des projets VCBuild.vcproj vers MSBuild (VCUpgrade.exe)|X|X|X|X|
|Optimisations guidées par profil|||X|X|

## <a name="debugging-features"></a>Fonctionnalités de débogage

|Fonctionnalité de débogage|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Débogage natif|X|X|X|X|
|natvis (visualisation de type natif)|X|X|X|X|
|Débogage graphique|X||X|X|
|Débogage managé||X|X|X|
|Utilisation du GPU|X||X|X|
|Utilisation de la mémoire|X||X|X|
|Remote Debugging|X|X|X|X|
|Débogage SQL|||X|X|
|Analyse statique du code|Limité|Limité|X|X|

## <a name="designers-and-editors"></a>Concepteurs et éditeurs

|Concepteur ou éditeur|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Concepteur XAML|X||X|X|
|Concepteur/éditeur de style CSS|X|X|X|X|
|Concepteur/éditeur HTML|X|X|X|X|
|Éditeur XML|X|X|X|X|
|Éditeur de code source|X|X|X|X|
|Fonctionnalités de productivité : refactorisation, IntelliSense, mise en forme de code C++|X|X|X|X|
|Concepteur Windows Forms||X|X|X|
|Concepteur de données|||X|X|
|Éditeur de ressources natives (fichiers .rc)|||X|X|
|Éditeurs de ressources|X|X|X|X|
|Éditeur de modèle|X||X|X|
|Concepteur Shader|X||X|X|

## <a name="data-features"></a>Fonctionnalités de données

|Fonctionnalité de données|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Concepteur de données|||X|X|
|Objets de données|||X|X|
|Services Web|||X|X|
|Explorateur de serveurs|||X|X|

## <a name="build-and-project-systems"></a>Systèmes de génération et de projet

|Fonctionnalité de génération ou de projet|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Générations en mode ligne de commande (msbuild.exe)|X|X|X|X|
|Multi-ciblage natif||X|X|X|
|Multi-ciblage managé||X|X|X|
|Générations en parallèle|X|X|X|X|
|Personnalisations de la build|X|X|X|X|
|Extensibilité des pages de propriétés|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automatisation et extensibilité

|Automatisation et extensibilité|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Modèles objet d'extensibilité|||X|X|
|Modèle de code|||X|X|
|Modèle de projet|||X|X|
|Modèle d'éditeur de ressources|||X|X|
|Modèle d'Assistant|||X|X|
|Modèle objet débogueur|||X|X|

## <a name="application-lifecycle-management-tools"></a>Outils de gestion du cycle de vie des applications

|Outil|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-|-|-|-|-|
|Tests unitaires (infrastructure native)|X|X|X|X|
|Tests unitaires (infrastructure managée)||X|X|X|
|Couverture du code||||X|
|Test manuel||||X|
|Tests exploratoires||||X|
|Gestion de cas de test||||X|
|Carte de code et graphiques de dépendance|||en lecture seule|X|
|Débogage des cartes de code||||X|

## <a name="see-also"></a>Voir aussi

[Installer Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Nouveautés de Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Types de projets C++ dans Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end
