---
title: "Contrôles ActiveX MFC : Avancées d’implémentation de la propriété | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5ac8b2cb1a9c8de43ecfbd2f4712d19750bb143a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Contrôles ActiveX MFC : implémentation des propriétés avancées
Cet article décrit les rubriques relatives à l’implémentation des propriétés avancées dans un contrôle ActiveX :  
  
-   [Propriétés en lecture seule et en écriture seule](#_core_read2donly_and_write2donly_properties)  
  
-   [Renvoi des codes d’erreur à partir d’une propriété](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a>Propriétés en lecture seule et en écriture seule  
 L’Assistant Ajout de propriété fournit une méthode rapide et simple pour implémenter des propriétés en lecture seule ou en écriture seule pour le contrôle.  
  
#### <a name="to-implement-a-read-only-or-write-only-property"></a>Pour implémenter une propriété en lecture seule ou en écriture seule  
  
1.  Chargez votre projet de contrôle.  
  
2.  Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.  
  
3.  Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.  
  
4.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.  
  
     Cette opération ouvre le [Assistant Ajout de propriété](../ide/names-add-property-wizard.md).  
  
5.  Dans le **nom de la propriété** , tapez le nom de votre propriété.  
  
6.  Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.  
  
7.  Dans le **Type de propriété** , sélectionnez le type approprié pour la propriété.  
  
8.  Si vous souhaitez une propriété en lecture seule, désactivez le nom de la fonction Set. Si vous souhaitez une propriété en écriture seule, désactivez le nom de la fonction Get.  
  
9. Cliquez sur **Terminer**.  
  
 Lorsque vous effectuez cette opération, l’Assistant Ajout de propriété insère la fonction `SetNotSupported` ou `GetNotSupported` dans l’entrée de mappage de distribution à la place d’un vecteur normal Set ou Get (fonction).  
  
 Si vous souhaitez modifier une propriété existante afin d’être en lecture seule ou en écriture seule, vous pouvez modifier manuellement de la table de dispatch et supprimer la fonction Set ou Get inutile à partir de la classe du contrôle.  
  
 Si vous souhaitez une propriété conditionnellement en lecture seule ou en écriture seule (par exemple, uniquement lorsque le contrôle s’exécute dans un mode particulier), vous pouvez fournir la fonction Set ou Get, comme d’habitude et appeler le `SetNotSupported` ou `GetNotSupported` fonction le cas échéant. Exemple :  
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 Cet exemple de code appelle `SetNotSupported` si le `m_bReadOnlyMode` membre de données est **TRUE**. Si **FALSE**, alors la propriété est définie sur la nouvelle valeur.  
  
##  <a name="_core_returning_error_codes_from_a_property"></a>Renvoi des Codes d’erreur à partir d’une propriété  
 Pour indiquer qu’une erreur s’est produite lors de la tentative obtenir ou définir une propriété, utilisez la `COleControl::ThrowError` (fonction), qui prend un `SCODE` (code d’état) en tant que paramètre. Vous pouvez utiliser prédéfini `SCODE` ou définir votre propre. Pour obtenir la liste de prédéfinis `SCODE`s et des instructions pour la définition personnalisé `SCODE`s, consultez [gestion des erreurs dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans les contrôles ActiveX : rubriques avancées.  
  
 Fonctions d’assistance existent pour la plus courante prédéfinie `SCODE`s, telles que [courants ;](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), et [COleControl :: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
> [!NOTE]
>  `ThrowError`est destiné à être utilisé uniquement comme un moyen de retourner une erreur à partir d’au sein Get d’une propriété ou Set fonction ou une méthode automation. Il s’agit de la seule fois où le Gestionnaire d’exceptions approprié sera présent sur la pile.  
  
 Pour plus d’informations sur les rapports d’exceptions dans d’autres zones du code, consultez [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) et la section [gestion des erreurs dans votre contrôle ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) dans l’article contrôles ActiveX : avancé Rubriques.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contrôles ActiveX MFC : propriétés](../mfc/mfc-activex-controls-properties.md)   
 [Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)   
 [COleControl, classe](../mfc/reference/colecontrol-class.md)
