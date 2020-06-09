---
title: 'Comment : personnaliser le bouton Application'
ms.date: 09/07/2019
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: 9160e602848adf8dc95c840d702e0b1a1b2f9049
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620040"
---
# <a name="how-to-customize-the-application-button"></a>Comment : personnaliser le bouton Application

Lorsque vous cliquez sur le bouton application, un menu de commandes s’affiche. En règle générale, le menu contient des commandes associées aux fichiers, telles que **ouvrir**, **Enregistrer**, **Imprimer**et **quitter**.

![Bouton Application de ruban MFC](../mfc/media/application_button.png "Bouton Application de ruban MFC")

Pour personnaliser le bouton de l’application, ouvrez-le dans la fenêtre **Propriétés** (dans **affichage des ressources**), modifiez ses propriétés, puis affichez un aperçu du contrôle du ruban.

### <a name="to-open-the-application-button-in-the-properties-window"></a>Pour ouvrir le bouton application dans le Fenêtre Propriétés

1. Dans Visual Studio, dans le menu **affichage** , cliquez sur **affichage des ressources**.

1. Dans **affichage des ressources**, double-cliquez sur la ressource du ruban pour l’afficher sur l’aire de conception.

1. Dans l’aire de conception, cliquez avec le bouton droit sur le menu du bouton de l’application, puis cliquez sur **Propriétés**.

## <a name="application-button-properties"></a>Propriétés du bouton d’application

Le tableau suivant définit les propriétés du bouton d’application.

|Propriété|Définition|
|--------------|----------------|
|**Boutons**|Contient la collection de trois boutons au maximum qui s’affichent dans le coin inférieur droit du menu de l’application.|
|**Caption**|Spécifie le texte du contrôle. Contrairement à d’autres éléments du ruban, le bouton d’application n’affiche pas de texte de légende. Au lieu de cela, le texte est utilisé pour l’accessibilité.|
|**Image HDPI**|Spécifie l’identificateur de l’icône du bouton d’application points par pouce (HDPI) élevé. Lorsque l’application s’exécute sur un moniteur haute résolution, **HDPI** est utilisé à la place de l' **image**.|
|**Images de grande taille HDPI**|Spécifie l’identificateur des grandes images haute résolution. Lorsque l’application s’exécute sur un moniteur haute résolution, **HDPI images de grande taille** est utilisée à la place d' **images volumineuses**.|
|**HDPI petites images**|Spécifie l’identificateur des petites images haute résolution. Lorsque l’application s’exécute sur un moniteur haute résolution, **HDPI** est utilisé à la place des **petites images**.|
|**Identifiant**|Spécifie l’identificateur du contrôle.|
|**Image**|Spécifie l’identificateur de l’icône de bouton d’application. L’icône est une bitmap 26x26 de 32 bits qui a une transparence alpha. Les parties transparentes de l’icône sont mises en surbrillance lorsque l’utilisateur clique sur le bouton de l’application ou le survole.|
|**Clés**|Spécifie la chaîne qui s’affiche lorsque la navigation dans les clés accélératrices est activée. La navigation dans les touches accélératrices est activée lorsque vous appuyez sur ALT.|
|**Images volumineuses**|Spécifie l’identificateur de l’image qui contient une série d’icônes 32 x 32. Les icônes sont utilisées par les boutons dans la collection d’éléments principale.|
|**Éléments principaux**|Contient une collection d’éléments de menu qui s’affichent dans le menu de l’application.|
|**Légende MRU**|Spécifie le texte affiché dans le panneau de liste récent.|
|**Petites images**|Spécifie l’identificateur de l’image qui contient une série d’icônes 16x16. Les icônes sont utilisées par les boutons de la collection de boutons.|
|**Utilisation**|Active ou désactive le panneau Liste récent. Le panneau Liste récent s’affiche dans le menu de l’application.|
|**Width**|Spécifie la largeur en pixels du panneau de liste récent.|

Le menu application n’apparaît pas sur l’aire de conception. Pour l’afficher, vous devez afficher un aperçu du ruban ou exécuter l’application.

#### <a name="to-preview-the-ribbon-control"></a>Pour afficher un aperçu du contrôle du ruban

- Dans la **barre d’outils**de l’éditeur de ruban, cliquez sur **tester le ruban**.

## <a name="see-also"></a>Voir aussi

[Concepteur de ruban (MFC)](ribbon-designer-mfc.md)
