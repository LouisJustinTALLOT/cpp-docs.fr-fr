---
title: Concepteur de ruban (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 1634eee30063a48041d60fc1b7116ca9543c9de2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511461"
---
# <a name="ribbon-designer-mfc"></a>Concepteur de ruban (MFC)

Le Concepteur de ruban permet de créer et de personnaliser des rubans dans les applications MFC. Un ruban est un élément d'interface utilisateur (IU) qui organise les commandes en groupes logiques. Ces groupes apparaissent sous des onglets distincts dans une bande transversale située dans la partie supérieure de la fenêtre. Le ruban remplace la barre de menus et les barres d'outils. Un ruban peut considérablement améliorer la convivialité d'une l'application. Pour plus d’informations, consultez [rubans](/windows/win32/uxguide/cmd-ribbons). L'illustration suivante représente un ruban.

![Contrôle de ressource de ruban MFC](../mfc/media/ribbon_no_callouts.png "Contrôle de ressource de ruban MFC")

Dans les versions antérieures de Visual Studio, les rubans devaient être créés en écrivant du code qui utilise les classes de ruban MFC telles que la [classe CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md). Dans Visual Studio 2010 et versions ultérieures, le concepteur de ruban fournit une autre méthode pour créer des rubans. Dans un premier temps, il convient de créer et de personnaliser un ruban en tant que ressource. Chargez ensuite la ressource de ruban à partir du code de l'application MFC. Vous pouvez même utiliser les ressources de ruban et les classes de ruban MFC conjointement. Par exemple, vous pouvez créer une ressource de ruban, puis y ajouter par programmation des éléments au moment de l’exécution à l’aide du code.

## <a name="understanding-the-ribbon-designer"></a>Présentation du Concepteur de ruban

Le Concepteur de ruban crée et stocke le ruban en tant que ressource. Quand vous créez une ressource de ruban, le Concepteur de ruban effectue trois opérations :

- Il ajoute une entrée dans le script de définition de ressources du projet (* .rc). Dans l’exemple suivant, IDR_RIBBON est le nom unique qui identifie la ressource de ruban, RT_RIBBON_XML est le type de ressource et Ribbon. mfcribbon-MS est le nom du fichier de ressources.

```
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Ajoute les définitions des ID de commande à resource.h.

```
#define IDR_RIBBON            307
```

- Crée un fichier de ressources de ruban (*.mfcribbon-ms) qui contient le code XML définissant les boutons, les contrôles et les attributs du ruban. Les modifications apportées au ruban dans le Concepteur de ruban sont stockées dans le fichier de ressources au format XML. L’exemple de code suivant montre une partie du contenu d' \*un fichier. mfcribbon-ms :

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Pour utiliser la ressource de ruban dans votre application MFC, chargez la ressource en appelant [CMFCRibbonBar :: LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Création d'un ruban à l'aide du Concepteur de ruban

Il existe deux façons d'ajouter une ressource de ruban à votre projet MFC :

- Créez une application MFC et configurez l'Assistant de projet MFC pour créer le ruban. Pour plus d’informations, consultez [Procédure pas à pas : Création d’une application de ruban à](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)l’aide de MFC.

- Dans un projet MFC existant, créez une ressource de ruban et chargez-la. Pour plus d’informations, consultez [Procédure pas à pas : Mise à jour de l’application Scribble MFC (partie 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)).

Si votre projet contient déjà un ruban codé manuellement, vous pouvez utiliser les fonctions de MFC pour convertir le ruban existant en ressource de ruban. Pour plus d'informations, voir [Procédure : Convertit un ruban MFC existant en ressource](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md)de ruban.

> [!NOTE]
>  Il n'est pas possible de créer des rubans dans des applications à base de boîtes de dialogue. Pour plus d’informations, consultez [type d’application, Assistant Application MFC](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Personnalisation des rubans

Pour ouvrir un ruban dans le Concepteur de ruban, double-cliquez sur la ressource de ruban dans l'Affichage des ressources. Dans le concepteur, vous pouvez ajouter, supprimer et personnaliser les éléments du ruban, le bouton d'application ou la barre d'outils Accès rapide. Vous pouvez aussi lier des événements, par exemple, des événements de clic de bouton et des événements de menu, à une méthode dans votre application.

L'illustration suivante représente les différents composants du Concepteur de ruban.

![Concepteur de ruban MFC](../mfc/media/ribbon_designer.png "Concepteur de ruban MFC")

- **Pratiques** Contient des contrôles qui peuvent être déplacés vers l’aire du concepteur.

- **Aire du concepteur :** Contient la représentation visuelle de la ressource de ruban.

- **Fenêtre Propriétés :** Répertorie les attributs de l’élément sélectionné dans l’aire du concepteur.

- **Affichage des ressources fenêtre :** Affiche les ressources qui incluent des ressources de ruban dans votre projet.

- **Barre d’outils de l’éditeur de ruban :** Contient des commandes qui vous permettent d’afficher un aperçu du ruban et de modifier son thème visuel.

Les rubriques suivantes expliquent comment utiliser les fonctionnalités du Concepteur de ruban :

- [Guide pratique pour Personnaliser le bouton Application](../mfc/how-to-customize-the-application-button.md)

- [Guide pratique pour Personnaliser la barre d’outils Accès rapide](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Guide pratique : Ajouter des contrôles de ruban et des gestionnaires d’événements](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Guide pratique : Charger une ressource du ruban à partir d’une application MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Définition des éléments de ruban

![Ruban MFC](../mfc/media/ribbon.png "Ruban MFC")

- **Bouton de l’application :** Bouton qui apparaît dans le coin supérieur gauche d’un ruban. Le bouton d'application remplace le menu Fichier et est visible même quand le ruban est réduit. Quand vous cliquez sur ce bouton, vous obtenez un menu qui contient une liste de commandes.

- **Barre d’outils accès rapide :** Une petite barre d’outils personnalisable qui affiche les commandes fréquemment utilisées.

- **Catégorie**: Regroupement logique qui représente le contenu d’un onglet de ruban.

- **Bouton par défaut de la catégorie :** Bouton qui apparaît sur le ruban lorsque le ruban est réduit. Quand vous cliquez sur ce bouton, la catégorie réapparaît sous forme de menu.

- **Panneau** Zone de la barre du ruban qui affiche un groupe de contrôles connexes. Chaque catégorie du ruban contient un ou plusieurs volets de ruban.

- **Éléments du ruban :** Contrôles dans les panneaux, par exemple, les boutons et les zones de liste déroulante. Pour afficher les différents contrôles qui peuvent être hébergés sur un ruban, [consultez exemple RibbonGadgets : Application](../overview/visual-cpp-samples.md)gadgets gadgets.

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](../mfc/user-interface-elements-mfc.md)<br/>
[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)
