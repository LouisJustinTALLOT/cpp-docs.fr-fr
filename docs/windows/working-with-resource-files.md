---
title: Utilisation des fichiers de ressources (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: 142a9120e0b6b95e659fcb47c275653fbefd8cbe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165884"
---
# <a name="working-with-resource-files"></a>Utilisation des fichiers de ressources

> [!WARNING]
> Cette section concerne les applications de bureau Windows écrites en C++.
>
> Pour plus d’informations sur les ressources des applications C++plateforme Windows universelle écrites dans, consultez [définition des ressources d’application](/windows/uwp/app-resources/), C++ou ajout de ressources aux projets/CLI (managés), consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le Guide du développeur .NET Framework.

Les ressources peuvent être composées d’un large éventail d’éléments, par exemple :

- Éléments d’interface qui fournissent des informations à l’utilisateur, telles qu’une bitmap, une icône ou un curseur.
- Ressources personnalisées qui contiennent des besoins en matière de données et d’applications.
- Ressources de version utilisées par les API d’installation.
- Ressources de menu et de boîte de dialogue.

Vous pouvez ajouter de nouvelles ressources à votre projet et modifier ces ressources à l'aide de l'éditeur de ressources approprié. La plupart des Assistants Visual C++ génèrent automatiquement un fichier .rc pour votre projet.

> [!NOTE]
> Les **éditeurs de ressources** et les **affichage des ressources** ne sont pas disponibles dans les éditions Express.

Pour ajouter manuellement des fichiers de ressources aux projets managés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Cet article explique comment accéder aux ressources, afficher des ressources statiques et assigner des chaînes de ressources à des propriétés.

Pour globaliser et localiser des ressources dans des applications gérées, consultez [globalisation et localisation d’applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="in-this-section"></a>Dans cette section

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
Décrit les fichiers de ressources et la façon dont ils sont utilisés dans les applications de bureau Windows. Fournit également des liens vers des articles qui décrivent comment utiliser des fichiers de ressources.

[Identificateurs de ressources (symboles)](../windows/symbols-resource-identifiers.md)<br/>
Décrit les symboles et fournit des informations sur l'utilisation de la boîte de dialogue **Symboles des ressources** pour gérer les symboles dans vos projets.

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
Décrit les éditeurs de ressources fournis dans Visual Studio et les types de ressources que vous pouvez modifier avec chaque éditeur. Fournit également des liens vers des informations détaillées sur l’utilisation de chaque éditeur.

## <a name="related-sections"></a>Sections connexes

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
Fournit des liens vers la documentation Visual C++.

[Nous contacter](/visualstudio/ide/talk-to-us)<br/>
Propose des liens vers des informations sur l'utilisation de l'ensemble de documentation, sur la sollicitation du support technique et sur l'emploi de fonctionnalités d'accessibilité.

## <a name="see-also"></a>Voir aussi

[Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md)<br/>
[Menus et autres ressources](/windows/win32/menurc/resources)
