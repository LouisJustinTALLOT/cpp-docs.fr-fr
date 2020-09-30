---
title: Ajout de fonctionnalités à l’aide des Assistants Code (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: 651eac8c630636455dd1ffa04fdd02b71fa3cf62
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509703"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Ajout de fonctionnalités à l’aide des Assistants Code (C++)

Après avoir créé un projet, vous pouvez changer ses fonctionnalités ou en ajouter d’autres. Parmi les tâches que vous pouvez effectuer, citons la création de classes, l’ajout de nouvelles fonctions et variables membres, ou encore l’ajout de méthodes et de propriétés Automation. Les Assistants Code sont conçus pour vous permettre d’effectuer toutes ces tâches.

> [!NOTE]
> Les Assistants de code ci-dessous, qui sont rarement utilisés, ont été supprimés dans Visual Studio 2019. La prise en charge générale d’ATL et MFC n’est pas affectée par la suppression de ces Assistants. Les exemples de code pour ces technologies sont archivés dans Microsoft Docs et dans le dépôt GitHub VCSamples.

- Assistant Composant COM+ 1.0 ATL
- Assistant Composant ASP ATL
- Assistant Fournisseur OLEDB ATL
- Assistant Page de propriétés ATL
- Assistant Consommateur OLEDB ATL
- Consommateur ODBC MFC
- Classe MFC à partir d’un contrôle ActiveX
- Classe MFC à partir d’une bibliothèque de types.

> [!NOTE]
> Vous pouvez ajouter des gestionnaires de messages et y mapper des messages et remplacer des fonctions virtuelles MFC à l’aide de l' [Assistant classe MFC](../mfc/reference/mfc-class-wizard.md).

## <a name="accessing-c-code-wizards"></a>Accès aux Assistants de code C++

Vous pouvez accéder aux Assistants de code C++ à partir de trois emplacements :

- Dans le menu **Projet**, utilisez la commande **Ajouter un nouvel élément** pour ouvrir la boîte de dialogue `Add New Item`. Celle-ci vous permet d’ajouter de nouveaux fichiers à votre projet. Utilisez la commande **Ajouter une classe** pour afficher la boîte de dialogue [Ajouter une classe](./adding-a-class-visual-cpp.md#add-class-dialog-box). Celle-ci ouvre des Assistants pour chaque type de classe que vous ajoutez à votre projet. Pour les classes MFC, utilisez l' [Assistant classe MFC](../mfc/reference/mfc-class-wizard.md). Utilisez la commande **Ajouter une ressource** pour afficher la boîte de dialogue [Ajouter une ressource](../windows/how-to-create-a-resource-script-file.md). Celle-ci vous permet de créer ou de sélectionner une ressource à ajouter à votre projet.

   Si vous mettez en surbrillance une classe ou une interface de votre projet dans Affichage de classes, le menu **Projet** affiche également les commandes suivantes :

  - **Implémenter l’interface** (à partir d’une classe de contrôle uniquement)

  - **Ajouter une fonction**

  - **Ajouter une variable**

  - **Ajouter un point de connexion** (classe ATL uniquement)

  - **Ajouter une méthode** (à partir d’une interface uniquement)

  - **Ajouter une propriété** (à partir d’une interface uniquement)

  - **Ajouter un événement** (à partir d’une classe de contrôle uniquement)

- Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur un dossier, puis cliquez sur **Ajouter** dans le menu contextuel pour ajouter des dossiers, éléments, classes, ressources, références web et fichiers, nouveaux ou existants, au projet.

- Dans la [fenêtre Affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nœud approprié, puis cliquez sur **Ajouter** dans le menu contextuel pour ajouter des fonctions, variables, classes, propriétés, méthodes, événements, interfaces, points de connexion ou autres éléments de code à votre projet.

   > [!NOTE]
   > Visual Studio ne propose pas d’Assistant pour l’ajout d’une interface à un projet. Vous pouvez ajouter une interface à un projet ATL ou [ajouter la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) en ajoutant un objet simple à l’aide de [l’Assistant Objet simple ATL](../atl/reference/atl-simple-object-wizard.md). Vous pouvez également ouvrir le fichier .idl du projet et créer l’interface en tapant :

    ```IDL
    interface IMyInterface {
    };
    ```

   Pour plus d’informations, consultez [Implémentation d’une interface](../ide/implementing-an-interface-visual-cpp.md) et [Ajout d’objets et de contrôles à un projet ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

   |Méthode utilisée pour accéder à l’Assistant de code|Description|
   |-----------------------------|-----------------|
   |Ajouter un nouvel élément|Les Assistants Code dans Ajouter un nouvel élément ajoutent des fichiers sources à votre projet. Si nécessaire, des répertoires supplémentaires sont créés aux emplacements dans lesquels le moteur de génération de projet s’attend à trouver les fichiers. Parmi les Assistants Code disponibles à partir de l’icône Ajouter un élément, citons les suivants :<br /><br />- Ajouter des fichiers sources C++ (.cpp, .h, .idl, .rc, .srf, .def, .rgs).<br />- Ajouter des fichiers de développement web (.html, .asp, .css, .xml).<br />- Ajouter des fichiers d’utilitaire et de ressources (.bmp, .cur, .ico, .rct, .sql, .txt).<br /><br />Ces Assistants Code ne sollicitent généralement pas d’informations, mais ils ajoutent un fichier à votre arborescence de développement. Vous pouvez renommer le fichier dans la fenêtre des propriétés.|
   |Explorateur de solutions|Les Assistants Code disponibles dans l’Explorateur de solutions varient selon l’endroit où se trouve le focus du curseur quand vous cliquez avec le bouton droit sur un élément. Si l’option **Ajouter** n’apparaît pas quand vous cliquez avec le bouton droit sur un élément, déplacez le curseur d’un niveau vers le haut dans l’arborescence de développement et réessayez. Les Assistants Code placent toujours le code supplémentaire à l’emplacement approprié dans l’arborescence de développement, quel que soit l’endroit où se trouve le curseur. Parmi les Assistants Code disponibles dans l’Explorateur de solutions, citons les suivants :<br /><br />-Add Class (ouvre la boîte de dialogue **Ajouter une classe** qui contient les nouveaux Assistants Code).<br />- Ajouter une ressource (Nouveau, Importer ou Personnaliser).<br />- Ajouter une référence web.|
   |Affichage de classes|Les Assistants Code disponibles dans Affichage de classes varient selon l’endroit où se trouve le focus du curseur quand vous cliquez avec le bouton droit sur un élément. Si l’option **Ajouter** n’apparaît pas quand vous cliquez avec le bouton droit sur un élément, déplacez le curseur d’un niveau vers le haut dans l’arborescence de classes et réessayez. Les Assistants Code placent toujours le code supplémentaire à l’emplacement approprié dans l’arborescence de développement, quel que soit l’endroit où se trouve le curseur. Parmi les Assistants Code disponibles dans Affichage de classes, citons les suivants :<br /><br />- [Ajouter une fonction membre](../ide/adding-a-member-function-visual-cpp.md).<br />- [Ajouter une variable membre](../ide/adding-a-member-variable-visual-cpp.md).<br />- [Ajouter une classe](../ide/adding-a-class-visual-cpp.md).<br />- [Implémenter l’interface](./implementing-an-interface-visual-cpp.md#implement-interface-wizard) (à partir d’une classe de contrôle uniquement)<br />- [Ajouter un point de connexion](./implementing-a-connection-point-visual-cpp.md#implement-connection-point-wizard) (classe ATL uniquement)<br />- [Ajouter une méthode](./adding-a-method-visual-cpp.md#add-method-wizard) (à partir d’une interface uniquement)<br />- [Ajouter une propriété](./adding-a-property-visual-cpp.md#names-add-property-wizard) (à partir d’une interface uniquement)<br />- [Ajouter un événement](./adding-an-event-visual-cpp.md#add-event-wizard) (à partir d’une classe de contrôle uniquement)<br /><br />Si vous sélectionnez Ajouter une classe, la boîte de dialogue **Ajouter une classe** s’ouvre. Celle-ci vous donne accès à tous les nouveaux Assistants Code Ajouter une classe.|

## <a name="see-also"></a>Voir aussi

[Substitution d’une fonction virtuelle](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Naviguer dans votre base de code C++ dans Visual Studio](../ide/navigate-code-cpp.md)<br>
[Types de projets C++ dans Visual Studio](../build/reference/visual-cpp-project-types.md)<br>
[Types de fichiers créés pour les projets Visual Studio C++](../build/reference/file-types-created-for-visual-cpp-projects.md)
