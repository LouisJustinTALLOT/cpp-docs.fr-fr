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
ms.openlocfilehash: 43a47366475b227ccfc5918b07760cc582326e82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387727"
---
# <a name="windows-desktop-wizard"></a>Assistant Windows Desktop

L’Assistant de bureau Windows remplace l’Assistant Application Win32 dans Visual Studio 2017 et versions ultérieures. L’Assistant vous permet de créer quatre types de projets C++ (répertoriées dans l’en-tête dans le tableau ci-dessous). Dans chaque cas, vous pouvez spécifier des options supplémentaires appropriées au type de projet que vous ouvrez. 

   ![Assistant Windows Desktop](media/windows-desktop-wizard.png)

Le tableau suivant indique les options disponibles pour chaque type d’application.

|Type de prise en charge|Application console|Application exécutable (Windows)|Bibliothèque de liens dynamiques|Bibliothèque statique|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Projet vide**|Oui|Oui|Oui|Non|
|**Symboles d’exportation**|Non|Non|Oui|Non|
|**En-tête précompilé**|Non|Non|Non|Oui|
|**prise en charge ATL**|Oui|Non|Non|Non|
|**prise en charge des MFC**|Oui|Non|Non|Oui|

## <a name="overview"></a>Vue d'ensemble

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
|**Application console**|Crée une application console. Programmes de console sont développées avec [fonctions de la Console](https://msdn.microsoft.com/library/ms813137.aspx), qui prennent en charge en mode caractère dans les fenêtres de console. Visual C++ [bibliothèques Runtime](../c-runtime-library/c-run-time-library-reference.md) également fournir la sortie et d’entrée à partir des fenêtres de console avec des fonctions d’e/s standard, telles que `printf_s()` et `scanf_s()`. Une application console n’a aucune interface utilisateur graphique. Il compile dans un fichier .exe et peut être exécuté comme une application autonome à partir de la ligne de commande.<br /><br /> Vous pouvez ajouter la prise en charge de MFC et ATL à une application de console.|
|**Application de Windows**|Crée un programme Win32. Un programme Win32 est une application exécutable (EXE) écrite en C ou C++, à l’aide d’appels à l’API Win32 pour créer une interface utilisateur graphique.<br /><br /> Vous ne pouvez pas ajouter MFC ou ATL prend en charge pour une application Windows.|
|**Bibliothèque de liens dynamiques**|Crée une bibliothèque de liens dynamiques (DLL) Win32. Une DLL Win32 est un fichier binaire écrit en C ou C++, qui utilise des appels à l’API Win32 plutôt qu’à des classes MFC et qui agit comme une bibliothèque partagée de fonctions pouvant être utilisé simultanément par plusieurs applications.<br /><br /> Vous ne pouvez pas ajouter la prise en charge MFC ou ATL à une application de la DLL créée à l’aide de cet Assistant, mais vous pouvez créer une DLL MFC en choisir **Nouveau > projet > DLL MFC**.|
|**Bibliothèque statique**|Crée une bibliothèque statique. Une bibliothèque statique est un fichier contenant des objets et leurs fonctions et les données qui établit un lien dans votre programme lorsque le fichier exécutable est généré. Cette rubrique explique comment créer les fichiers de démarrage et [propriétés de projet](../build/reference/property-pages-visual-cpp.md) pour une bibliothèque statique. Un fichier de bibliothèque statique offre les avantages suivants :<br /><br />-Une bibliothèque statique Win32 est utile si l’application que vous travaillez sur effectue des appels à l’API Win32 plutôt qu’à des classes MFC.<br />-Le processus de liaison est le même si le reste de votre application Windows est écrite en C ou en C++.<br />-Vous pouvez lier une bibliothèque statique à un programme basé sur MFC ou à un programme non-MFC.|

## <a name="additional-options"></a>Options supplémentaires

Définit la prise en charge et les options de l’application, en fonction de son type.

|Option|Description|
|------------|-----------------|
|**Projet vide**|Spécifie que les fichiers projet sont vides. Si vous avez un ensemble de fichiers de code source (par exemple, les fichiers .cpp, fichiers d’en-tête, icônes, barres d’outils, boîtes de dialogue et ainsi de suite) et que vous souhaitez créer un projet dans l’environnement de développement Visual C++, vous devez d’abord créer un projet vide, puis ajoutez les fichiers au projet.<br /><br /> Cette sélection n’est pas disponible pour les projets de bibliothèque statique.|
|**Symboles d’exportation**|Spécifie que le projet de DLL exporte des symboles.|
|**En-tête précompilé**|Spécifie que le projet de bibliothèque statique utilise un en-tête précompilé.|
|**Vérifie de Security Development Lifecycle (SDL)**|Pour plus d’informations sur SDL, consultez [Guide de processus Microsoft Security Development Lifecycle (SDL)](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>Ajouter des en-têtes communs pour :

Ajouter la prise en charge pour l’une des bibliothèques fournies dans Visual C++.

|Option|Description|
|------------|-----------------|
|**ATL**|Intègre la prise en charge de projet pour les classes dans la bibliothèque ATL (Active Template). Pour les applications console Win32 uniquement.<br /><br /> **Remarque** cette option n’indique pas de prise en charge pour l’ajout d’objets ATL à l’aide de la bibliothèque ATL les Assistants de code. Vous pouvez ajouter des objets ATL uniquement aux projets ATL ou MFC des projets avec ATL prennent en charge.|
|**MFC**|Intègre la prise en charge de projet pour la bibliothèque Microsoft Foundation classes (MFC). Pour les applications console Win32 et des bibliothèques statiques.|

## <a name="remarks"></a>Notes

Une fois que vous avez créé une application de bureau Windows, vous pouvez ajouter des classes C++ génériques à l’aide de l’ [Assistant Classe C++ générique](../ide/generic-cpp-class-wizard.md) . Vous pouvez ajouter d’autres éléments, tels que des fichiers HTML, des fichiers d’en-tête, des ressources ou des fichiers texte.

> [!NOTE]
> Vous ne pouvez pas ajouter de classes ATL. En outre, vous ne pouvez ajouter de classes MFC qu’aux types d’application de bureau Windows qui prennent en charge MFC (consultez le tableau précédent).

Vous pouvez afficher les fichiers que l’Assistant a créés pour votre projet dans **l’Explorateur de solutions**. Pour plus d’informations sur les fichiers que l’Assistant crée pour votre projet, consultez le fichier projet généré, `ReadMe.txt`. Pour plus d’informations sur les types de fichier, consultez [Types de fichier créés pour les projets Visual C++](../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Voir aussi

[Types de projets Visual C++](../build/reference/visual-cpp-project-types.md)