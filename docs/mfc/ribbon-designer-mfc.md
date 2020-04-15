---
title: Concepteur de ruban (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 8b66ff0f19392eb1685f8632a3fc4d9e90094304
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372800"
---
# <a name="ribbon-designer-mfc"></a>Concepteur de ruban (MFC)

Le Concepteur de ruban permet de créer et de personnaliser des rubans dans les applications MFC. Un ruban est un élément d'interface utilisateur (IU) qui organise les commandes en groupes logiques. Ces groupes apparaissent sous des onglets distincts dans une bande transversale située dans la partie supérieure de la fenêtre. Le ruban remplace la barre de menus et les barres d'outils. Un ruban peut considérablement améliorer la convivialité d'une l'application. Pour plus d’informations, voir [Rubans](/windows/win32/uxguide/cmd-ribbons). L'illustration suivante représente un ruban.

![Contrôle de ressources de ruban MFC](../mfc/media/ribbon_no_callouts.png "Contrôle de ressources de ruban MFC")

Dans les versions précédentes de Visual Studio, des rubans ont dû être créés en écrivant du code qui utilise les classes de ruban MFC telles que [cmFCRibbonBar Class](../mfc/reference/cmfcribbonbar-class.md). Dans Visual Studio 2010 et plus tard, le concepteur de rubans fournit une méthode alternative pour la construction de rubans. Dans un premier temps, il convient de créer et de personnaliser un ruban en tant que ressource. Chargez ensuite la ressource de ruban à partir du code de l'application MFC. Vous pouvez même utiliser les ressources de ruban et les classes de ruban MFC conjointement. Par exemple, vous pouvez créer une ressource de ruban et y ajouter par programmation des éléments supplémentaires au moment de l'exécution en utilisant du code.

## <a name="understanding-the-ribbon-designer"></a>Présentation du Concepteur de ruban

Le Concepteur de ruban crée et stocke le ruban en tant que ressource. Quand vous créez une ressource de ruban, le Concepteur de ruban effectue trois opérations :

- Il ajoute une entrée dans le script de définition de ressources du projet (* .rc). Dans l’exemple suivant, IDR_RIBBON est le nom unique qui identifie la ressource ruban, RT_RIBBON_XML est le type de ressource, et ribbon.mfcribbon-ms est le nom du fichier de ressources.

```cpp
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Ajoute les définitions des ID de commande à resource.h.

```
#define IDR_RIBBON            307
```

- Crée un fichier de ressources de ruban (*.mfcribbon-ms) qui contient le code XML définissant les boutons, les contrôles et les attributs du ruban. Les modifications apportées au ruban dans le Concepteur de ruban sont stockées dans le fichier de ressources au format XML. L’exemple de code suivant montre \*une partie du contenu d’un fichier .mfcribbon-ms :

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Pour utiliser la ressource ruban dans votre application MFC, chargez la ressource en appelant [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Création d'un ruban à l'aide du Concepteur de ruban

Il existe deux façons d'ajouter une ressource de ruban à votre projet MFC :

- Créez une application MFC et configurez l'Assistant de projet MFC pour créer le ruban. Pour plus d’informations, voir [Procédure pas à pas: Créer une application ruban en utilisant MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- Dans un projet MFC existant, créez une ressource de ruban et chargez-la. Pour plus d’informations, voir [Procédure pas à pas : Mise à jour de l’application MFC Scribble (Partie 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).

Si votre projet contient déjà un ruban codé manuellement, vous pouvez utiliser les fonctions de MFC pour convertir le ruban existant en ressource de ruban. Pour plus d’informations, voir [comment : Convertir un ruban MFC existant en une ressource ruban](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).

> [!NOTE]
> Il n'est pas possible de créer des rubans dans des applications à base de boîtes de dialogue. Pour plus d’informations, voir [Type d’application, MFC Application Wizard](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Personnalisation des rubans

Pour ouvrir un ruban dans le Concepteur de ruban, double-cliquez sur la ressource de ruban dans l'Affichage des ressources. Dans le concepteur, vous pouvez ajouter, supprimer et personnaliser les éléments du ruban, le bouton d'application ou la barre d'outils Accès rapide. Vous pouvez aussi lier des événements, par exemple, des événements de clic de bouton et des événements de menu, à une méthode dans votre application.

L'illustration suivante représente les différents composants du Concepteur de ruban.

![Concepteur de ruban MFC](../mfc/media/ribbon_designer.png "Concepteur de ruban MFC")

- **Boîte à outils:** Contient des commandes qui peuvent être traînés à la surface du concepteur.

- **Surface du concepteur:** Contient la représentation visuelle de la ressource ruban.

- ** [Assistant de classe](reference/mfc-class-wizard.md):** Répertorie les attributs de l’élément sélectionné sur la surface du concepteur.

- **Fenêtre De vue des ressources :** Affiche les ressources qui incluent les ressources ruban, dans votre projet.

- **Barre d’outils de l’éditeur de ruban :** Contient des commandes qui vous permettent de prévisualiser le ruban et de changer son thème visuel.

Les rubriques suivantes expliquent comment utiliser les fonctionnalités du Concepteur de ruban :

- [Comment : personnaliser le bouton Application](../mfc/how-to-customize-the-application-button.md)

- [Guide pratique pour personnaliser la barre d’outils Accès rapide](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Comment : ajouter des contrôles de ruban et des gestionnaires d'événements](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Comment : charger une ressource du ruban à partir d'une application MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Définition des éléments de ruban

![Ruban MFC](../mfc/media/ribbon.png "Ruban MFC")

- **Bouton d’application :** Le bouton qui apparaît sur le coin supérieur gauche d’un ruban. Le bouton d'application remplace le menu Fichier et est visible même quand le ruban est réduit. Quand vous cliquez sur ce bouton, vous obtenez un menu qui contient une liste de commandes.

- **Barre d’outils d’accès rapide :** Une petite barre d’outils personnalisable qui affiche fréquemment des commandes utilisées.

- **Catégorie**: Le regroupement logique qui représente le contenu d’un onglet ruban.

- **Bouton par défaut de catégorie :** Le bouton qui apparaît sur le ruban lorsque le ruban est réduit au minimum. Quand vous cliquez sur ce bouton, la catégorie réapparaît sous forme de menu.

- **Panel:** Une zone de la barre de ruban qui affiche un groupe de contrôles connexes. Chaque catégorie du ruban contient un ou plusieurs volets de ruban.

- **Éléments du ruban :** Contrôles dans les panneaux, par exemple, boutons et boîtes combo. Pour voir les différents contrôles qui peuvent être hébergés sur un ruban, voir [RibbonGadgets Sample: Ribbon Gadgets Application](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Éléments d’interface utilisateur](../mfc/user-interface-elements-mfc.md)<br/>
[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)
