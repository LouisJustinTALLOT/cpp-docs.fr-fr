---
title: 'Comment : personnaliser le bouton d’Application | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 828886e6a5c4891e1fd7e1d820ee00542e052cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-the-application-button"></a>Comment : personnaliser le bouton Application
Lorsque vous cliquez sur le bouton d’Application, un menu de commandes s’affiche. En règle générale, le menu contient relatives aux fichiers de commandes telles que **ouvrir**, **enregistrer**, **impression**, et **Exit**.  
  
 ![Bouton Application de ruban MFC](../mfc/media/application_button.png "application_button")  
  
 Pour personnaliser le bouton d’Application, l’ouvrir dans le **propriétés** fenêtre, modifiez ses propriétés, puis affichez l’aperçu du contrôle de ruban.  
  
### <a name="to-open-the-application-button-in-the-properties-window"></a>Pour ouvrir le bouton d’Application dans la fenêtre Propriétés  
  
1.  Dans Visual Studio, sur le **vue** menu, cliquez sur **affichage des ressources**.  
  
2.  Dans **affichage des ressources**, double-cliquez sur la ressource de ruban pour l’afficher dans l’aire de conception.  
  
3.  Dans l’aire de conception, cliquez sur le menu du bouton Application, puis sur **propriétés**.  
  
## <a name="application-button-properties"></a>Propriétés de l’application  
 Le tableau suivant définit les propriétés du bouton d’Application.  
  
|Propriété|Définition|  
|--------------|----------------|  
|**Boutons**|Contient la collection de jusqu'à trois boutons qui apparaissent dans le coin inférieur droit du menu Application.|  
|**Légende**|Spécifie le texte du contrôle. Contrairement à d’autres éléments de ruban, le bouton d’Application n’affiche pas de texte de légende. Au lieu de cela, le texte est utilisé pour l’accessibilité.|  
|**HDPI Image**|Spécifie l’identificateur des haute points par pouce icône du bouton (HDPI) Application. Lorsque l’application s’exécute sur un moniteur de PPP élevé, **HDPI Image** est utilisé à la place de **Image**.|  
|**HDPI Large Images**|Spécifie l’identificateur d’images de grande taille PPP élevés. Lorsque l’application s’exécute sur un moniteur de PPP élevé, **HDPI Large Images** est utilisé à la place de **grandes Images**.|  
|**HDPI Small Images**|Spécifie l’identificateur des images petites PPP élevés. Lorsque l’application s’exécute sur un moniteur de PPP élevé, **HDPI Small Images** est utilisé à la place de **petites Images**.|  
|**ID**|Spécifie l’identificateur du contrôle.|  
|**Image**|Spécifie l’identificateur de l’icône de bouton d’Application. L’icône est un bitmap de 26 x 26 32 bits qui a une transparence alpha. Les parties transparentes de l’icône sont mis en surbrillance lorsqu’un clic sur le bouton d’Application ou le survole.|  
|**Clés**|Spécifie la chaîne qui s’affiche lorsque l’info-bulle de clé de la navigation est activée. Conseil à la clé de navigation est activée lorsque vous appuyez sur ALT.|  
|**Images de grande taille**|Spécifie l’identificateur de l’image qui contient une série d’icônes de 32 x 32. Les icônes sont utilisées par les boutons dans la collection d’éléments de principal.|  
|**Éléments principaux**|Contient une collection d’éléments de menu qui s’affichent dans le menu Application.|  
|**MRU Caption**|Spécifie le texte affiché dans le volet de la liste récents.|  
|**Petites Images**|Spécifie l’identificateur de l’image qui contient une série d’icônes 16 x 16. Les icônes sont utilisées par les boutons dans la collection de boutons.|  
|**Utilisez**|Active ou désactive le volet de la liste récents. Le panneau de la liste récents apparaît dans le menu Application.|  
|**Largeur**|Spécifie la largeur en pixels du volet Liste récents.|  
  
 Le menu de l’Application n’apparaît pas sur l’aire de conception. Pour l’afficher, vous devez afficher un aperçu du ruban ou exécuter l’application.  
  
#### <a name="to-preview-the-ribbon-control"></a>Pour afficher un aperçu du contrôle de ruban  
  
-   Sur le **barre d’outils Éditeur Ribbon**, cliquez sur **Test ruban**.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)

