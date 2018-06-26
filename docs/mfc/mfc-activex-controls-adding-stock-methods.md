---
title: 'Contrôles ActiveX MFC : Ajout de méthodes Stock | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2005391c6d91ee09703194eb8b8062ecfe08ba77
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929797"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Contrôles ActiveX MFC : ajout de méthodes stock
Une méthode stock diffère d’une méthode personnalisée dans la mesure où il est déjà implémenté par la classe [COleControl](../mfc/reference/colecontrol-class.md). Par exemple, `COleControl` contient une fonction membre prédéfinie qui prend en charge la méthode d’actualisation de votre contrôle. L’entrée de mappage de dispatch pour cette méthode stock est DISP_STOCKFUNC_REFRESH.  
  
 `COleControl` prend en charge deux méthodes stock : DoClick et Refresh. Refresh est appelée par l’utilisateur du contrôle pour mettre immédiatement à jour l’apparence du contrôle ; DoClick est appelée pour déclencher Click du contrôle l’événement.  
  
|Méthode|Entrée de table de dispatch|Commentaire|  
|------------|------------------------|-------------|  
|`DoClick`|**(DE DISP_STOCKPROP_DOCLICK)**|Déclenche un événement Click.|  
|`Refresh`|**(DE DISP_STOCKPROP_REFRESH)**|Mise à jour immédiate de l’apparence du contrôle.|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a> Ajout d’une méthode Stock à l’aide de l’Assistant Ajout de méthode  
 Ajout d’une méthode stock est simple à l’aide de la [Assistant Ajout de méthode](../ide/add-method-wizard.md). La procédure suivante illustre l’ajout de la méthode d’actualisation pour un contrôle créé à l’aide de l’Assistant de contrôle ActiveX MFC.  
  
#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Pour ajouter la méthode stock Refresh à l’aide de l’Assistant Ajout de méthode  
  
1.  Chargez votre projet de contrôle.  
  
2.  Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.  
  
3.  Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.  
  
4.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une méthode**.  
  
     L’Assistant Ajout de méthode s’ouvre.  
  
5.  Dans le **nom de la méthode** , cliquez sur **Actualiser**.  
  
6.  Cliquez sur **Terminer**.  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a> Méthode modifications effectuées Assistant Ajout de méthodes Stock  
 Étant donné que la méthode stock Refresh est prise en charge par la classe de base du contrôle, la **Assistant Ajout de méthode** ne modifie pas la déclaration de classe du contrôle en aucune façon. Il ajoute une entrée pour la méthode à la table de dispatch du contrôle et à ses. Fichier IDL. La ligne suivante est ajoutée à la table de dispatch du contrôle, située dans son implémentation (. Fichier de RPC) :  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 Cela rend la méthode d’actualisation disponibles pour les utilisateurs du contrôle.  
  
 La ligne suivante est ajoutée à du contrôle. Fichier IDL :  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 Cette ligne assigne un numéro d’identification spécifique à la méthode d’actualisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

