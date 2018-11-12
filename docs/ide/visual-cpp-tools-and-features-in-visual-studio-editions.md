---
title: Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio
ms.date: 02/28/2018
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 7f40e59ae3e5e883827a212a16d1dd19822dc136
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463750"
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio

Les tableaux suivants présentent les fonctionnalités Visual C++ disponibles dans Visual Studio. La présence d'une croix (« X ») dans une cellule indique que la fonctionnalité est disponible ; une cellule vide indique que la fonctionnalité n'est pas disponible. Les remarques entre parenthèses indiquent qu'une fonctionnalité est disponible, mais limitée.

## <a name="platforms"></a>Plateformes

||||||
|-|-|-|-|-|
|Plateforme|Visual Studio Express pour Windows 10|Visual Studio Express pour Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Bureau Windows||X|X|X|
|Plateforme Windows universelle ((téléphone, tablette, PC, Xbox, IoT et HoloLens))|X||X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Compilateurs

|Compilateur|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Compilateur X86 32 bits|X|X|X|X|
|Compilateur croisé X86_arm|X||X|X|
|Compilateur x64 64 bits|||X|X|
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
|OpenMP|X|X|X|X|

## <a name="project-templates"></a>Modèles de projet

|Modèle|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Modèles XAML pour UWP, Windows 8.1, Windows Phone 8.0|X||X|X|
|Applications Direct3D|X||X|X|
|DLL (Windows universel)|X||X|X|
|Bibliothèque statique (Windows universel)|X||X|X|
|Composant Windows Runtime|X||X|X|
|Application de tests unitaires (Windows universel)|X||X|X|
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
|Débogage distant|X|X|X|X|
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
|éditeurs de ressources|X|X|X|X|
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

||||||
|-|-|-|-|-|
|Outil|Visual Studio Express pour Windows|Visual Studio Express pour Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
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
[Types de projets Visual C++](../ide/visual-cpp-project-types.md)<br/>
[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686)<br/>
