---
title: Création d’une DLL de ressources uniquement
description: Comment créer une DLL de ressources uniquement dans Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821341"
---
# <a name="creating-a-resource-only-dll"></a>Création d’une DLL de ressources uniquement

Une DLL de ressources uniquement est une DLL qui ne contient que des ressources, telles que des icônes, des bitmaps, des chaînes et des boîtes de dialogue. L’utilisation d’une DLL de ressources uniquement est un bon moyen de partager le même ensemble de ressources entre plusieurs programmes. C’est également un bon moyen de fournir une application avec des ressources localisées pour plusieurs langues. Pour plus d’informations, consultez [ressources localisées dans les applications MFC : dll satellites](localized-resources-in-mfc-applications-satellite-dlls.md).

## <a name="create-a-resource-only-dll"></a>Créer une DLL de ressource uniquement

Pour créer une DLL de ressource uniquement, vous devez créer un nouveau projet DLL Windows (non-MFC) et ajouter vos ressources au projet :

::: moniker range="vs-2015"

1. Sélectionnez **projet Win32** dans la boîte de dialogue **nouveau projet** . Entrez le nom du projet et de la solution, puis choisissez **OK**.

1. Dans l **'Assistant application Win32**, sélectionnez Paramètres de l' **application**. Choisissez un **type** d’application **dll**. Sous **Options supplémentaires**, sélectionnez **Projet vide**. Choisissez **Terminer** pour créer votre projet.

1. Créez un script de ressources qui contient les ressources de la DLL (comme une chaîne ou un menu). Enregistrez le fichier `.rc`.

1. Dans le menu **projet** , sélectionnez **Ajouter un élément existant**, puis insérez le nouveau fichier de `.rc` dans le projet.

1. Spécifiez l’option [/noentry](reference/noentry-no-entry-point.md) de l’éditeur de liens. `/NOENTRY` empêche l’éditeur de liens de lier une référence à `_main` dans la DLL ; Cette option est requise pour créer une DLL de ressources uniquement.

1. Créez la DLL.

::: moniker-end
::: moniker range=">=vs-2017"

1. Sélectionnez **Windows Desktop Wizard** dans la boîte de dialogue **nouveau projet** et choisissez **suivant**. Dans la page **configurer votre nouveau projet** , entrez les noms de projet et de solution, puis choisissez **créer**.

1. Dans la boîte de dialogue **projet de bureau Windows** , sélectionnez un **type d’application** **bibliothèque de liens dynamiques**. Sous **Options supplémentaires**, sélectionnez **Projet vide**. Choisissez **OK** pour créer votre projet.

1. Créez un script de ressources qui contient les ressources de la DLL (comme une chaîne ou un menu). Enregistrez le fichier `.rc`.

1. Dans le menu **projet** , sélectionnez **Ajouter un élément existant**, puis insérez le nouveau fichier de `.rc` dans le projet.

1. Spécifiez l’option [/noentry](reference/noentry-no-entry-point.md) de l’éditeur de liens. `/NOENTRY` empêche l’éditeur de liens de lier une référence à `_main` dans la DLL ; Cette option est requise pour créer une DLL de ressources uniquement.

1. Créez la DLL.

::: moniker-end

## <a name="use-a-resource-only-dll"></a>Utiliser une DLL de ressource uniquement

L’application qui utilise la DLL de ressource uniquement doit appeler [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md) ou une fonction associée pour établir une liaison explicite à la dll. Pour accéder aux ressources, appelez les fonctions génériques `FindResource` et `LoadResource`, qui fonctionnent sur n’importe quel type de ressource. Ou appelez l’une des fonctions spécifiques aux ressources suivantes :

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

L’application doit appeler `FreeLibrary` lorsqu’elle a fini d’utiliser les ressources.

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)\
[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
