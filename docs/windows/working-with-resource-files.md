---
title: Utilisation des fichiers de ressources (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: 09a85231f871ef1a21b2f2adb309d94bb4a29e1a
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504510"
---
# <a name="working-with-resource-files"></a>Utilisation des fichiers de ressources

> [!WARNING]
> Cette section concerne les applications de bureau Windows écrites en C++.
>
> Pour plus d’informations sur les ressources dans les applications de plateforme Windows universelle écrites en C++, consultez [définition des ressources d’application](/windows/uwp/app-resources/), ou sur l’ajout de ressources à C++ / c++ / CLI (géré), projets, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le .NET Framework Guide du développeur.

Ressources peuvent être composées d’un large éventail d’éléments, tels que :

- Les éléments d’interface qui fournissent des informations à l’utilisateur comme une image bitmap, une icône ou un curseur.
- Ressources personnalisées qui contiennent des données et l’application a besoin.
- Ressources de version qui sont utilisées par le programme d’installation de l’API.
- Ressources de zone de menu et de la boîte de dialogue.

Vous pouvez ajouter de nouvelles ressources à votre projet et modifier ces ressources à l'aide de l'éditeur de ressources approprié. La plupart des Assistants Visual C++ génèrent automatiquement un fichier .rc pour votre projet.

> [!NOTE]
> Le **éditeurs de ressources** et **affichage des ressources** ne sont pas disponibles dans les éditions Express.

Pour ajouter manuellement les fichiers de ressources aux projets managés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Cet article comprend comment accéder aux ressources, afficher des ressources statiques et affecter des chaînes de ressources aux propriétés.

Pour globaliser et localiser les ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="in-this-section"></a>Dans cette section

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
Décrit les fichiers de ressources et comment ils sont utilisés dans les applications de bureau Windows. Fournit également des liens vers des articles qui expliquent comment utiliser des fichiers de ressources.

[Identificateurs de ressources (symboles)](../windows/symbols-resource-identifiers.md)<br/>
Décrit les symboles et fournit des informations sur l'utilisation de la boîte de dialogue **Symboles des ressources** pour gérer les symboles dans vos projets.

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
Décrit les éditeurs de ressources fournis dans Visual Studio et les types de ressources que vous pouvez modifier avec chaque éditeur. Fournit également des liens vers des informations détaillées sur l’utilisation de chaque éditeur.

## <a name="related-sections"></a>Rubriques connexes

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
Fournit des liens vers la documentation Visual C++.

[Nous contacter](/visualstudio/ide/talk-to-us)<br/>
Propose des liens vers des informations sur l'utilisation de l'ensemble de documentation, sur la sollicitation du support technique et sur l'emploi de fonctionnalités d'accessibilité.

## <a name="see-also"></a>Voir aussi

[Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md)<br/>
[Menus et autres ressources](/windows/desktop/menurc/resources)