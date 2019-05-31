---
title: Détermination des DLL à redistribuer
ms.date: 03/25/2019
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
ms.openlocfilehash: 4e4b53745c76a8e5b630bdd92633779e84262188
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451266"
---
# <a name="determining-which-dlls-to-redistribute"></a>Détermination des DLL à redistribuer

Quand vous créez une application qui utilise les DLL de bibliothèque fournies par Visual Studio, ces mêmes DLL doivent aussi être présentes sur les ordinateurs des utilisateurs de votre application pour que celle-ci puisse s’exécuter. Comme il est probable que la plupart des utilisateurs n'ont pas installé Visual Studio, vous devez les leur fournir. Visual Studio met à disposition ces DLL sous forme de *fichiers redistribuables* que vous pouvez inclure dans le programme d’installation de votre application.

Pour qu’il vous soit plus facile d’inclure les DLL redistribuables dans votre programme d’installation, elles sont aussi disponibles sous forme de *packages redistribuables* autonomes. Il s’agit d’exécutables propres à l’architecture qui utilisent un déploiement central pour installer les fichiers redistribuables sur l’ordinateur d’un utilisateur. Par exemple, vcredist\_x86.exe installe les bibliothèques de 32 bits pour x86 ordinateurs, vcredist\_x64.exe installe les bibliothèques de 64 bits pour x64 ordinateurs et vcredist\_ARM.exe installe les bibliothèques pour les ordinateurs ARM. Nous recommandons un déploiement central, car Microsoft peut utiliser le service Windows Update pour mettre à jour ces bibliothèques indépendamment. En plus de la copie dans votre installation de Visual Studio, les packages redistribuables actuels sont disponibles au téléchargement. Pour afficher des liens vers les packages redistribuables les plus récents pris en charge pour les ensembles d’outils actuels et plus anciens, consultez [Derniers téléchargements pris en charge de Visual C++](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads). Vous trouverez des versions antérieures spécifiques des packages redistribuables en recherchant « Packages redistribuables Visual C++ » dans le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=158431).

Le numéro de la version principale du package redistribuable que vous déployez doit correspondre à la version de l’ensemble d’outils Visual Studio qui a servi à créer votre application et la version secondaire doit être identique ou supérieure. Visual Studio 2017 et Visual Studio 2015 ont des numéros de version d’ensemble d’outils compatibles, ce qui signifie que les fichiers redistribuables Visual Studio 2017 peuvent être utilisés par des applications générées à l’aide de l’ensemble d’outils 2015. Même s’ils peuvent être compatibles, nous ne prenons pas en charge l’utilisation des fichiers redistribuables 2015 dans les applications générées à l’aide de l’ensemble d’outils 2017. Nous prenons uniquement en charge l’utilisation d’un package redistribuable qui est identique ou plus récent que la version de votre ensemble d’outils.

Une autre façon d’inclure les DLL redistribuables dans votre programme d’installation consiste à utiliser les *modules de fusion*. Ces modules Microsoft Installer sont inclus dans le programme d’installation de votre application et installés par celui-ci. Les modules de fusion pour les DLL redistribuables figurent dans votre répertoire d’installation de Visual Studio sous \\VC\\Redist\MSVC\\*version*\\MergeModules\\. Dans les versions antérieures de Visual Studio, ces fichiers se trouvent dans le répertoire \\Program Files ou \\Program Files (x86) dans un sous-répertoire Common Files\\Merge Modules. Pour plus d’informations sur l’utilisation de ces fichiers, consultez [Redistribution des composants à l’aide de modules de fusion](redistributing-components-by-using-merge-modules.md).

Les DLL redistribuables individuelles sont également incluses dans votre installation de Visual Studio. Par défaut, elles sont installées dans le répertoire d’installation de Visual Studio dans le dossier \\VC\\Redist\\MSVC\\*version*. Les numéros de *version* peuvent représenter différents numéros de build mineure d’un seul ensemble commun de fichiers redistribuables. Utilisez la dernière version de n’importe quel fichier DLL de bibliothèque, package redistribuable ou module de fusion trouvé dans ces répertoires. Vous pouvez utiliser ces bibliothèques pour un déploiement local, en les installant dans le même répertoire que votre application. Nous déconseillons le déploiement local, car vous devez fournir les mises à jour à vos applications déployées. Un déploiement central avec des packages redistribuables est préférable.

Pour identifier les DLL à redistribuer avec votre application, collectez une liste des DLL dont dépend votre application. Elles sont normalement indiquées comme entrées de la bibliothèque d’importation dans l’éditeur de liens. Certaines bibliothèques, telles que vcruntime et UCRT (Universal C Runtime), sont incluses par défaut. Si votre application ou l’une de ses dépendances utilise LoadLibrary pour charger dynamiquement une DLL, cette DLL peut ne pas figurer dans les entrées dans l’éditeur de liens. Une façon de collecter la liste des DLL chargées dynamiquement est d’exécuter l’outil Dependency Walker (depends.exe) sur votre application, comme indiqué dans [Fonctionnement des dépendances d’une application Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Malheureusement, cet outil est obsolète et risque de signaler qu’il ne peut pas trouver certaines DLL.

Dès que vous avez la liste de dépendances, comparez-la à la liste liée dans le fichier Redist.txt qui figure sous le répertoire d’installation de Microsoft Visual Studio ou à la « liste REDIST » de DLL redistribuables référencée dans la section « Fichiers de code distribuable » des termes du contrat de licence logiciel Microsoft de votre copie de Visual Studio. Pour Visual Studio 2017, consultez [Code distribuable pour Microsoft Visual Studio 2017 (inclut les utilitaires, l’extensibilité et les fichiers BuildServer)](https://go.microsoft.com/fwlink/p/?linkid=823098). Pour Visual Studio 2015, consultez [Code distribuable pour Microsoft Visual Studio 2015 et pour le SDK Microsoft Visual Studio 2015 (inclut les utilitaires et les fichiers BuildServer)](https://go.microsoft.com/fwlink/p/?linkid=799794). Pour Visual Studio 2013, la liste est disponible en ligne dans [Code distribuable pour Microsoft Visual Studio 2013 et pour le SDK Microsoft Visual Studio 2013](https://go.microsoft.com/fwlink/p/?LinkId=313603).

Dans les versions de Visual Studio antérieures à Visual Studio 2015, la bibliothèque CRT (C Runtime) a été incluse en tant que DLL redistribuable, dans msvc*version*.dll. À partir de Visual Studio 2015, les fonctions dans la bibliothèque CRT ont été refactorisées dans vcruntime et UCRT. La bibliothèque UCRT est désormais un composant système dans Windows 10, géré par Windows Update. Elle est disponible sur tous les systèmes d’exploitation Windows 10. Pour déployer votre application sur des systèmes d’exploitation antérieurs, vous devrez peut-être redistribuer également la bibliothèque UCRT. Une version antérieure de la bibliothèque UCRT est incluse dans les fichiers redistribuables Visual Studio, qui est installée uniquement sur les systèmes d’exploitation antérieurs à Windows 10 et seulement si aucune version de la bibliothèque UCRT n’est déjà installée. Pour obtenir une version installable de la bibliothèque UCRT pour les systèmes de niveau inférieur en tant que package de mise à jour du système Microsoft, consultez [Windows 10 Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=48234) dans le Centre de téléchargement Microsoft.

Vous ne pouvez pas redistribuer tous les fichiers inclus dans Visual Studio ; vous êtes uniquement autorisé à redistribuer les fichiers spécifiés dans Redist.txt ou dans la « liste REDIST » en ligne. Les versions Debug des applications et les diverses DLL de débogage Visual C++ ne sont pas redistribuables. Pour plus d’informations, consultez [Choix d’une méthode de déploiement](choosing-a-deployment-method.md).

Le tableau suivant décrit certaines des DLL Visual C++ dont votre application peut dépendre.

|Bibliothèque Visual C++|Description|S'applique à|
|--------------------------|-----------------|----------------|
|vcruntime*version*.dll|Bibliothèque Runtime pour le code natif.|Applications qui utilisent les services de démarrage et d’arrêt des langages C et C++ standard.|
|vccorlib*version*.dll|Bibliothèque Runtime pour le code managé.|Applications qui utilisent les services de langage C++ pour le code managé.|
|msvcp*version*.dll et msvcp*version*_*dotnumber*.dll|Bibliothèque standard C++ pour le code natif.|Applications qui utilisent la [bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md).|
|concrt*version*.dll|Bibliothèque runtime d’accès concurrentiel pour le code natif.|Applications qui utilisent le [runtime d’accès concurrentiel](../parallel/concrt/concurrency-runtime.md).|
|mfc*version*.dll|Bibliothèque MFC (Microsoft Foundation Class).|Applications qui utilisent la [bibliothèque MFC](../mfc/mfc-desktop-applications.md).|
|mfc*version* *language*.dll|Ressources de bibliothèque MFC (Microsoft Foundation Class).|Applications qui utilisent des ressources de langage spécifiques pour MFC.|
|mfc*version*u.dll|Bibliothèque MFC avec prise en charge Unicode.|Applications qui utilisent la [bibliothèque MFC](../mfc/mfc-desktop-applications.md) et nécessitent une prise en charge Unicode.|
|mfcmifc80.dll|Bibliothèque d'interfaces gérées MFC.|Applications qui utilisent la [bibliothèque MFC](../mfc/mfc-desktop-applications.md) avec les [contrôles Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*version*.dll|Bibliothèque managée MFC.|Applications qui utilisent la [bibliothèque MFC](../mfc/mfc-desktop-applications.md) avec les [contrôles Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*version*u.dll|Bibliothèque managée MFC avec prise en charge Unicode.|Applications qui utilisent la [bibliothèque MFC](../mfc/mfc-desktop-applications.md) avec les [contrôles Windows Forms](/dotnet/framework/winforms/controls/index) et qui nécessitent une prise en charge Unicode.|
|vcamp*version*.dll|Bibliothèque AMP pour le code natif.|Applications qui utilisent le code de la [bibliothèque C++ AMP](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).|
|vcomp*version*.dll|Bibliothèque OpenMP pour le code natif.|Applications qui utilisent le code de la [bibliothèque C++ OpenMP](../parallel/openmp/openmp-in-visual-cpp.md).|

> [!NOTE]
> Vous n'avez plus besoin de redistribuer Active Template Library sous forme de DLL distincte. Sa fonctionnalité a été déplacée dans les en-têtes et une bibliothèque statique.

Pour plus d’informations sur la redistribution de ces DLL avec votre application, consultez [Redistribution des fichiers Visual C++](redistributing-visual-cpp-files.md). Pour obtenir des exemples, consultez [Exemples de déploiement](deployment-examples.md).

En règle générale, vous n'avez pas besoin de redistribuer les DLL système, car elles font partie intégrante du système d'exploitation. Toutefois, il peut y avoir des exceptions, par exemple, lorsque votre application doit s'exécuter sur plusieurs versions de systèmes d'exploitation Microsoft. Dans ce cas, veillez à lire les termes du contrat de licence correspondants. De même, essayez d'effectuer la mise à niveau des DLL système via Windows Update, les Service Packs ou les packages redistribuables proposés par Microsoft.

## <a name="see-also"></a>Voir aussi

[Choix d’une méthode de déploiement](choosing-a-deployment-method.md)<br/>
[Déploiement des applications de bureau](deploying-native-desktop-applications-visual-cpp.md)
