---
title: Assistant Windows Desktop
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 47984b4c4416bf129efb226381fe778659aa16ca
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503515"
---
# <a name="windows-desktop-wizard"></a>Assistant Windows Desktop

L’Assistant Windows Desktop remplace l’Assistant application Win32 dans Visual Studio 2017 et versions ultérieures. L’Assistant vous permet de créer l’un des quatre types de projets C++ (listés dans l’en-tête du tableau ci-dessous). Dans chaque cas, vous pouvez spécifier des options supplémentaires appropriées au type de projet que vous ouvrez.

   ![Assistant Windows Desktop](media/windows-desktop-wizard.png)

Le tableau suivant indique les options disponibles pour chaque type d’application.

|Type de prise en charge|Application de console|Application exécutable (Windows)|Bibliothèque de liens dynamiques|Bibliothèque statique|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Projet vide**|Oui|Oui|Oui|Non|
|**Symboles d’exportation**|Non|Non|Oui|Non|
|**En-tête précompilé**|Non|Non|Non|Oui|
|**prise en charge ATL**|Oui|Non|Non|Non|
|**prise en charge des MFC**|Oui|Non|Non|Oui|

## <a name="overview"></a>Vue d’ensemble

La page de l’Assistant décrit les paramètres de projet actuels de l’application Win32 que vous créez. Par défaut, les options suivantes sont définies :

- Le projet est une application Windows.

- Le projet n’est pas vide.

- Le projet ne contient aucun symbole d’exportation.

- Le projet n’utilise pas de fichier d’en-tête précompilé (cette option est disponible pour les projets de bibliothèque statique uniquement).

- Le projet n’inclut pas la prise en charge de MFC ni d’ATL.

## <a name="application-type"></a>Type d'application

Crée le type d’application spécifié.

|Option|Description|
|------------|-----------------|
|**Application console**|Crée une application console. Les bibliothèques Runtime Visual C++ fournissent également une sortie et [une](../c-runtime-library/c-run-time-library-reference.md) entrée à partir de fenêtres de console avec des fonctions d’e/s standard, telles que `printf_s()` et `scanf_s()` . Une application console n’a pas d’interface utilisateur graphique. Elle compile dans un fichier. exe et peut être exécutée en tant qu’application autonome à partir de la ligne de commande.<br /><br /> Vous pouvez ajouter la prise en charge MFC et ATL à une application console.|
|**Application Windows**|Crée un programme Win32. Un programme Win32 est une application exécutable (EXE) écrite en C ou C++, à l’aide d’appels à l’API Win32 pour créer une interface utilisateur graphique.<br /><br /> Vous ne pouvez pas ajouter la prise en charge MFC ou ATL à une application Windows.|
|**Bibliothèque de liens dynamiques**|Crée une bibliothèque de liens dynamiques (DLL) Win32. Une DLL Win32 est un fichier binaire, écrit en C ou C++, qui utilise des appels à l’API Win32 plutôt qu’aux classes MFC, et qui agit comme une bibliothèque partagée de fonctions qui peuvent être utilisées simultanément par plusieurs applications.<br /><br /> Vous ne pouvez pas ajouter la prise en charge MFC ou ATL à une application DLL créée à l’aide de cet Assistant, mais vous pouvez créer une DLL MFC en choisissant **nouveau > projet > DLL MFC**.|
|**Bibliothèque statique**|Crée une bibliothèque statique. Une bibliothèque statique est un fichier contenant des objets, ainsi que leurs fonctions et données, qui sont liées à votre programme lors de la génération du fichier exécutable. Cette rubrique explique comment créer les fichiers de démarrage et les [Propriétés de projet](../build/reference/property-pages-visual-cpp.md) pour une bibliothèque statique. Un fichier de bibliothèque statique offre les avantages suivants :<br /><br />-Une bibliothèque statique Win32 est utile si l’application sur laquelle vous travaillez effectue des appels à l’API Win32 plutôt qu’à des classes MFC.<br />-Le processus de liaison est le même que le reste de votre application Windows soit écrit en C ou en C++.<br />-Vous pouvez lier une bibliothèque statique à un programme MFC ou à un programme non-MFC.|

## <a name="additional-options"></a>Options supplémentaires

Définit la prise en charge et les options de l’application, en fonction de son type.

|Option|Description|
|------------|-----------------|
|**Projet vide**|Spécifie que les fichiers projet sont vides. Si vous avez un ensemble de fichiers de code source (tels que des fichiers. cpp, des fichiers d’en-tête, des icônes, des barres d’outils, des boîtes de dialogue, etc.) et que vous souhaitez créer un projet dans l’environnement de développement Visual C++, vous devez d’abord créer un projet vide, puis ajouter les fichiers au projet.<br /><br /> Cette sélection n’est pas disponible pour les projets de bibliothèque statique.|
|**Symboles d’exportation**|Spécifie que le projet de DLL exporte des symboles.|
|**En-tête précompilé**|Spécifie que le projet de bibliothèque statique utilise un en-tête précompilé.|
|**Contrôles du cycle de vie de développement de la sécurité (SDL)**|Pour plus d’informations sur SDL, consultez [Microsoft Security Development Lifecycle (SDL) le Guide de processus](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>Ajoutez des en-têtes communs pour :

Ajoutez la prise en charge de l’une des bibliothèques fournies dans Visual C++.

|Option|Description|
|------------|-----------------|
|**ATL**|S’appuie sur la prise en charge du projet pour les classes dans le Active Template Library (ATL). Pour les applications console Win32 uniquement.<br /><br /> **Remarque** Cette option n’indique pas la prise en charge de l’ajout d’objets ATL à l’aide des assistants code ATL. Vous pouvez ajouter des objets ATL uniquement aux projets ATL ou aux projets MFC avec la prise en charge ATL.|
|**MFC**|S’appuie sur la prise en charge du projet pour la bibliothèque MFC (Microsoft Foundation Class). Pour les applications console Win32 et les bibliothèques statiques uniquement.|

## <a name="remarks"></a>Remarques

Une fois que vous avez créé une application de bureau Windows, vous pouvez ajouter des classes C++ génériques à l’aide de l’ [Assistant Classe C++ générique](../ide/adding-a-generic-cpp-class.md#generic-c-class-wizard) . Vous pouvez ajouter d’autres éléments, tels que des fichiers HTML, des fichiers d’en-tête, des ressources ou des fichiers texte.

> [!NOTE]
> Vous ne pouvez pas ajouter de classes ATL. En outre, vous ne pouvez ajouter de classes MFC qu’aux types d’application de bureau Windows qui prennent en charge MFC (consultez le tableau précédent).

Vous pouvez afficher les fichiers que l’Assistant a créés pour votre projet dans **l’Explorateur de solutions**. Pour plus d’informations sur les fichiers créés par l’Assistant pour votre projet, consultez le fichier généré par le projet, `ReadMe.txt` . Pour plus d’informations sur les types de fichiers, les [types de fichiers créés pour les projets Visual Studio C++](../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Voir aussi

[Types de projets C++ dans Visual Studio](../build/reference/visual-cpp-project-types.md)
