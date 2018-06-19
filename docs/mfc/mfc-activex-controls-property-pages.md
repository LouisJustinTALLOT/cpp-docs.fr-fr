---
title: 'Contrôles ActiveX MFC : Pages de propriétés | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81d28a7c5fdb48201cc1f4f2998fd0904749445d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351743"
---
# <a name="mfc-activex-controls-property-pages"></a>Contrôles ActiveX MFC : pages de propriétés
Pages de propriétés permettent à un utilisateur du contrôle ActiveX afficher et modifier les propriétés du contrôle ActiveX. Ces propriétés sont accessibles en appelant une boîte de dialogue Propriétés du contrôle, qui contient une ou plusieurs pages de propriétés qui fournissent une interface graphique personnalisée pour afficher et modifier les propriétés du contrôle.  
  
 Pages de propriétés du contrôle ActiveX sont affichées de deux manières :  
  
-   Lors de verbe de propriétés du contrôle (**OLEIVERB_PROPERTIES**) est appelé, le contrôle ouvre une boîte de dialogue de propriétés modale qui contient les pages de propriétés du contrôle.  
  
-   Le conteneur peut afficher sa propre boîte de dialogue non modale qui affiche les pages de propriétés du contrôle sélectionné.  
  
 La boîte de dialogue de propriétés (illustrée dans la figure suivante) se compose d’une zone pour afficher des onglets de basculer entre les pages de propriétés et une collection de boutons qui effectuent des tâches courantes telles que la fermeture de la boîte de dialogue page de propriété, de la page de propriétés en cours, annulation des modifications effectuées, ou immédiatement en appliquant les modifications du contrôle ActiveX.  
  
 ![Boîte de dialogue de propriétés pour Circ3](../mfc/media/vc373i1.gif "vc373i1")  
Boîte de dialogue Propriétés  
  
 Cet article traite des rubriques relatives à l’aide des pages de propriétés dans un contrôle ActiveX. Elles incluent notamment :  
  
-   [Implémentation de la page de propriété par défaut pour un contrôle ActiveX](#_core_implementing_the_default_property_page)  
  
-   [Ajout de contrôles à une page de propriétés](#_core_adding_controls_to_a_property_page)  
  
-   [Personnalisation de la fonction DoDataExchange](#_core_customizing_the_dodataexchange_function)  
  
 Pour plus d’informations sur l’utilisation des pages de propriétés dans un contrôle ActiveX, consultez les articles suivants :  
  
-   [Contrôles ActiveX MFC : ajout d’une page de propriétés personnalisées](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [Contrôles ActiveX MFC : utilisation des pages de propriétés stock](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 Pour plus d’informations sur l’utilisation des feuilles de propriétés dans une application MFC autre qu’un contrôle ActiveX, consultez [feuilles de propriétés](../mfc/property-sheets-mfc.md).  
  
##  <a name="_core_implementing_the_default_property_page"></a> Implémentation de la Page de propriété par défaut  
 Si vous utilisez l’Assistant contrôle ActiveX pour créer votre projet de contrôle, l’Assistant contrôle ActiveX fournit une classe de page de propriétés par défaut pour le contrôle dérivé [COlePropertyPage classe](../mfc/reference/colepropertypage-class.md). Au départ, cette page de propriétés est vide, mais vous pouvez ajouter n’importe quel contrôle de boîte de dialogue ou un ensemble de contrôles à ce dernier. Étant donné que l’Assistant contrôle ActiveX crée la classe de page qu’une seule propriété par défaut, les classes de page de propriétés supplémentaires (également dérivé `COlePropertyPage`) doit être créé à l’aide de la vue de la classe. Pour plus d’informations sur cette procédure, consultez [contrôles ActiveX MFC : ajout d’une autre Page personnalisée propriété](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).  
  
 Implémentation d’une propriété page (dans ce cas, la valeur par défaut) est un processus en trois étapes :  
  
#### <a name="to-implement-a-property-page"></a>Pour implémenter une page de propriétés  
  
1.  Ajouter un `COlePropertyPage`-pour le projet de contrôle de la classe dérivée. Si le projet a été créé à l’aide de l’Assistant contrôle ActiveX (comme dans ce cas), la classe de page de propriétés par défaut existe déjà.  
  
2.  Utilisez l’éditeur de boîte de dialogue pour ajouter des contrôles pour le modèle de page de propriétés.  
  
3.  Personnaliser le `DoDataExchange` fonction de la `COlePropertyPage`-classe pour échanger des valeurs entre le contrôle de page de propriété et le contrôle ActiveX dérivée.  
  
 Par exemple à des fins, les procédures suivantes utilisent un contrôle simple (nommé « Exemple »). Exemple a été créé à l’aide de l’Assistant contrôle ActiveX et contient uniquement la propriété stock Caption.  
  
##  <a name="_core_adding_controls_to_a_property_page"></a> Ajout de contrôles à une Page de propriétés  
  
#### <a name="to-add-controls-to-a-property-page"></a>Pour ajouter des contrôles à une page de propriétés  
  
1.  Ouvrez votre projet de contrôle, ouvrez l’affichage des ressources.  
  
2.  Double-cliquez sur le **boîte de dialogue** icône active.  
  
3.  Ouvrez le **IDD_PROPPAGE_SAMPLE** boîte de dialogue.  
  
     L’Assistant contrôle ActiveX ajoute le nom du projet à la fin de l’ID de boîte de dialogue, dans ce cas, un exemple.  
  
4.  Glisser -déplacer le contrôle sélectionné à partir de la boîte à outils vers la zone de la boîte de dialogue.  
  
5.  Pour cet exemple, un texte d’étiquette contrôle « Caption : » et un contrôle de zone d’édition avec un **IDC_CAPTION** identificateur sont suffisantes.  
  
6.  Cliquez sur **enregistrer** sur la barre d’outils pour enregistrer vos modifications.  
  
 Maintenant que l’interface utilisateur a été modifié, vous devez lier la zone d’édition avec la propriété de légende. Cette opération est effectuée dans la section suivante en modifiant le `CSamplePropPage::DoDataExchange` (fonction).  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a> Personnalisation de la fonction DoDataExchange  
 Votre page de propriétés [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) fonction vous permet de lier des valeurs de page de propriétés avec les valeurs réelles des propriétés du contrôle. Pour établir des liens, vous devez mapper les champs de page de propriété approprié à leurs propriétés respectives du contrôle.  
  
 Ces mappages sont implémentées à l’aide de la page de propriétés **DDP_** fonctions. Le **DDP_** fonctions fonctionnent comme les **DDX_** fonctions utilisées dans les boîtes de dialogue MFC standards, avec une exception. En plus de la référence à une variable membre, **DDP_** fonctions acceptent le nom de la propriété du contrôle. Voici une entrée de type dans le `DoDataExchange` (fonction) pour une page de propriétés.  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 Cette fonction associe la page de propriétés `m_caption` variable membre avec la légende, à l’aide de la `DDP_TEXT` (fonction).  
  
 Après avoir configuré le contrôle de page de propriété inséré, vous devez établir un lien entre le contrôle de page de propriétés, `IDC_CAPTION`, et à l’aide de la propriété du contrôle réel, la légende, la **DDP_Text** comme décrit ci-dessus.  
  
 [Pages de propriétés](../mfc/reference/property-pages-mfc.md) sont disponibles pour d’autres types de contrôle de boîte de dialogue, telles que les cases à cocher, cases d’option et les zones de liste. Le tableau ci-dessous répertorie l’ensemble de la page de propriétés **DDP_** fonctions et leurs objectifs :  
  
### <a name="property-page-functions"></a>Fonctions de la Page de propriétés  
  
|Nom de la fonction|Utilisez cette fonction pour lier|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|Index de la chaîne sélectionnée dans une zone de liste modifiable avec une propriété du contrôle.|  
|`DDP_CBString`|La chaîne sélectionnée dans une zone de liste modifiable avec une propriété du contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de propriété, mais n’est pas forcément il entièrement.|  
|`DDP_CBStringExact`|La chaîne sélectionnée dans une zone de liste modifiable avec une propriété du contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|  
|`DDP_Check`|Une case à cocher avec une propriété du contrôle.|  
|`DDP_LBIndex`|Index de la chaîne sélectionnée dans une zone de liste avec une propriété du contrôle.|  
|`DDP_LBString`|La chaîne sélectionnée dans une zone de liste avec une propriété du contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de propriété, mais n’est pas forcément il entièrement.|  
|`DDP_LBStringExact`|La chaîne sélectionnée dans une zone de liste avec une propriété du contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|  
|`DDP_Radio`|Bouton radio avec une propriété du contrôle.|  
|**DDP_TEXT**|Texte avec une propriété du contrôle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage, classe](../mfc/reference/colepropertypage-class.md)
