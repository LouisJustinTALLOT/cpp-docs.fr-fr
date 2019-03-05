---
title: 'Procédure : Personnaliser le bouton d’Application'
ms.date: 11/19/2018
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: d45ceaf1cce21f77871e966e0e8f525f95cb4c37
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269531"
---
# <a name="how-to-customize-the-application-button"></a>Procédure : Personnaliser le bouton d’Application

Lorsque vous cliquez sur le bouton d’Application, un menu de commandes s’affiche. En règle générale, le menu contient des commandes relatives aux fichiers tels que **Open**, **enregistrer**, **impression**, et **Exit**.

![Bouton Application de ruban MFC](../mfc/media/application_button.png "bouton Application de ruban MFC")

Pour personnaliser le bouton d’Application, ouvrez-le dans le **propriétés** fenêtre, modifier ses propriétés, puis affichez l’aperçu du contrôle de ruban.

### <a name="to-open-the-application-button-in-the-properties-window"></a>Pour ouvrir le bouton d’Application dans la fenêtre Propriétés

1. Dans Visual Studio, sur le **vue** menu, cliquez sur **affichage des ressources**.

1. Dans **affichage des ressources**, double-cliquez sur la ressource de ruban pour l’afficher sur l’aire de conception.

1. Dans l’aire de conception, cliquez sur le menu du bouton Application, puis sur **propriétés**.

## <a name="application-button-properties"></a>Propriétés de l’application

Le tableau suivant définit les propriétés du bouton d’Application.

|Propriété|Définition|
|--------------|----------------|
|**Boutons**|Contient la collection de trois boutons qui apparaissent dans l’angle inférieur droit du menu d’Application.|
|**Légende**|Spécifie le texte du contrôle. Contrairement à d’autres éléments de ruban, le bouton d’Application n’affiche pas de texte de légende. Au lieu de cela, le texte est utilisé pour l’accessibilité.|
|**HDPI Image**|Spécifie l’identificateur des haute points par pouce icône du bouton Application de (HDPI). Lorsque l’application s’exécute sur un moniteur de PPP élevé, **HDPI Image** est utilisé au lieu de **Image**.|
|**HDPI Large Images**|Spécifie l’identificateur des haute résolution grandes images. Lorsque l’application s’exécute sur un moniteur de PPP élevé, **HDPI Large Images** est utilisé au lieu de **grandes Images**.|
|**HDPI Small Images**|Spécifie l’identificateur des haute résolution petites images. Lorsque l’application s’exécute sur un moniteur de PPP élevé, **HDPI Small Images** est utilisé au lieu de **petites Images**.|
|**ID**|Spécifie l’identificateur du contrôle.|
|**Image**|Spécifie l’identificateur de l’icône de bouton d’Application. L’icône est un bitmap de 26 x 26 de 32 bits qui a la transparence alpha. Les parties transparentes de l’icône sont mises en surbrillance lorsque l’utilisateur clique sur le bouton d’Application ou le survole.|
|**Clés**|Spécifie la chaîne qui s’affiche lorsque l’info-bulle de clé de la navigation est activée. Navigation de l’info-bulle de clé est activée lorsque vous appuyez sur ALT.|
|**Images de grande taille**|Spécifie l’identificateur de l’image qui contient une série d’icônes de 32 x 32. Les icônes sont utilisées par les boutons dans la collection d’éléments de Main.|
|**Éléments principaux**|Contient une collection d’éléments de menu qui s’affichent dans le menu de l’Application.|
|**MRU Caption**|Spécifie le texte affiché dans le volet liste récente.|
|**Petites Images**|Spécifie l’identificateur de l’image qui contient une série d’icônes 16 x 16. Les icônes sont utilisées par les boutons dans la collection de boutons.|
|**Utilisation**|Active ou désactive le volet liste récente. Le panneau de liste récente s’affiche dans le menu de l’Application.|
|**Width**|Spécifie la largeur en pixels du panneau liste récente.|

Le menu de l’Application n’apparaît pas sur l’aire de conception. Pour l’afficher, vous devez afficher un aperçu du ruban ou exécuter l’application.

#### <a name="to-preview-the-ribbon-control"></a>Pour afficher un aperçu du contrôle de ruban

- Sur le **barre d’outils Éditeur Ribbon**, cliquez sur **Test ruban**.

## <a name="see-also"></a>Voir aussi

[Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)
