---
title: 'Contrôles ActiveX MFC : Ajout de propriétés personnalisées | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7facc4c712d070cffe9be5f07a236b2b04b972e9
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931913"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Contrôles ActiveX MFC : ajout de propriétés personnalisées
Propriétés personnalisées la différence des propriétés stock de propriétés personnalisées ne sont pas déjà implémentées par la `COleControl` classe. Une propriété personnalisée est utilisée pour exposer un état ou une apparence d’un contrôle ActiveX à un programmeur utilisant le contrôle.  
  
 Cet article explique comment ajouter une propriété personnalisée pour le contrôle ActiveX à l’aide de l’Assistant Ajout de propriété et explique les modifications de code qui en résulte. Les rubriques traitées ici sont les suivantes :  
  
-   [À l’aide de l’Assistant Ajout de propriété pour ajouter une propriété personnalisée](#_core_using_classwizard_to_add_a_custom_property)  
  
-   [Ajouter des modifications de l’Assistant de propriété pour les propriétés personnalisées](#_core_classwizard_changes_for_custom_properties)  
  
 Propriétés personnalisées existent en quatre variantes d’implémentation : Variable membre, une Variable membre avec Notification, méthodes Get/Set et paramétrables.  
  
-   Implémentation des variables membres  
  
     Cette implémentation représente l’état de la propriété sous la forme d’une variable de membre dans la classe du contrôle. Utiliser l’implémentation de Variable membre lorsqu’il n’est pas important de savoir quand la valeur de propriété change. Les trois types, cette implémentation crée le moins de code de prise en charge pour la propriété. Pour l’implémentation des variables membres, la macro d’entrée de la table de dispatch est [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).  
  
-   Variable membre avec l’implémentation de Notification  
  
     Cette implémentation se compose d’une variable membre et une fonction de notification créée par l’Assistant Ajout de propriété. La fonction de notification est appelée automatiquement par le framework après la valeur de propriété change. Utilise la Variable membre avec l’implémentation de la Notification lorsque vous avez besoin d’être averti une fois une valeur de propriété a changé. Cette implémentation nécessite plus de temps, car elle requiert un appel de fonction. Pour cette implémentation, la macro d’entrée de la table de dispatch est [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).  
  
-   Implémentation des méthodes de Get/Set  
  
     Cette implémentation se compose d’une paire de fonctions membres de la classe du contrôle. L’implémentation des méthodes Get/Set appelle automatiquement l’obtention de membre fonction lorsque l’utilisateur du contrôle demande la valeur actuelle de la propriété et la fonction membre quand l’utilisateur du contrôle demande que de modifier la propriété. Utilisez cette implémentation lorsque vous le souhaitez pour calculer la valeur d’une propriété au moment de l’exécution, valider une valeur passée par l’utilisateur du contrôle avant de modifier la propriété réelle ou implémenter un type de propriété en lecture - ou en écriture seule. Pour cette implémentation, la macro d’entrée de la table de dispatch est [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex). La section suivante, [à l’aide de l’Assistant Ajout de propriété pour ajouter une propriété personnalisée](#_core_using_classwizard_to_add_a_custom_property), utilise la propriété personnalisée CircleOffset pour illustrer cette implémentation.  
  
-   Implémentation paramétrée  
  
     Implémentation paramétrée est prise en charge par l’Assistant Ajout de propriété. Une propriété paramétrée (parfois appelée un tableau de propriétés) peut être utilisée pour accéder à un ensemble de valeurs via une seule propriété de votre contrôle. Pour cette implémentation, la macro d’entrée de la table de dispatch est DISP_PROPERTY_PARAM. Pour plus d’informations sur l’implémentation de ce type, consultez [implémentation d’une propriété paramétrable](../mfc/mfc-activex-controls-advanced-topics.md) dans l’article contrôles ActiveX : rubriques avancées.  
  
##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> À l’aide de l’Assistant Ajout de propriété pour ajouter une propriété personnalisée  
 La procédure suivante illustre l’ajout d’une propriété personnalisée, CircleOffset, qui utilise l’implémentation de méthodes Get/Set. La propriété personnalisée CircleOffset permet à l’utilisateur du contrôle décaler le cercle à partir du centre du rectangle englobant du contrôle. La procédure d’ajout de propriétés personnalisées avec une implémentation d’un autre que les méthodes Get/Set est très similaire.  
  
 Cette procédure peut également être utilisée pour ajouter d’autres propriétés personnalisées que vous souhaitez. Remplacez le nom de votre propriété personnalisée pour les paramètres et le nom de la propriété CircleOffset.  
  
#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Pour ajouter la propriété personnalisée CircleOffset à l’aide de l’Assistant Ajout de propriété  
  
1.  Chargez votre projet de contrôle.  
  
2.  Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.  
  
3.  Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.  
  
4.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.  
  
     Cette opération ouvre le [Assistant Ajout de propriété](../ide/names-add-property-wizard.md).  
  
5.  Dans le **nom de la propriété** , tapez *CircleOffset*.  
  
6.  Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.  
  
7.  Dans le **Type de propriété** boîte, sélectionnez **court**.  
  
8.  Tapez un nom unique pour vos fonctions Get et Set, ou acceptez les noms par défaut.  
  
9. Cliquez sur **Terminer**.  
  
##  <a name="_core_classwizard_changes_for_custom_properties"></a> Ajouter un Assistant de propriété est modifiée pour les propriétés personnalisées  
 Lorsque vous ajoutez la propriété personnalisée CircleOffset, l’Assistant Ajout de propriété apporte des modifications à l’en-tête (. (H) et l’implémentation (. (CPP) de la classe du contrôle.  
  
 Les lignes suivantes sont ajoutées à la. Fichier H pour déclarer deux fonctions appelées `GetCircleOffset` et `SetCircleOffset`:  
  
 [!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]  
  
 La ligne suivante est ajoutée à votre contrôle de code. Fichier IDL :  
  
 [!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]  
  
 Cette ligne assigne à la propriété CircleOffset un numéro d’identification spécifique, obtenue à partir de la position dans la liste des méthodes et propriétés de l’Assistant Ajout de propriété.  
  
 En outre, la ligne suivante est ajoutée à la table de dispatch (dans le. Cpp de la classe du contrôle) pour mapper la propriété CircleOffset aux deux fonctions de gestionnaire du contrôle :  
  
 [!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]  
  
 Enfin, les implémentations de la `GetCircleOffset` et `SetCircleOffset` fonctions sont ajoutées à la fin du contrôle. Fichier CPP. Dans la plupart des cas, vous allez modifier la fonction Get pour retourner la valeur de la propriété. La fonction Set contient généralement le code qui doit être exécuté avant ou après les modifications de propriété.  
  
 [!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]  
  
 Notez que l’Assistant Ajout de propriété ajoute automatiquement un appel, de [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag), le corps de la fonction. Appel de cette fonction marque le contrôle comme modifiée. Si un contrôle a été modifié, son nouvel état est enregistré lorsque le conteneur est enregistré. Cette fonction doit être appelée chaque fois qu’une propriété, enregistrée en tant que partie de l’état du contrôle persistant, change de valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contrôles ActiveX MFC : propriétés](../mfc/mfc-activex-controls-properties.md)   
 [Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)   
 [COleControl, classe](../mfc/reference/colecontrol-class.md)
