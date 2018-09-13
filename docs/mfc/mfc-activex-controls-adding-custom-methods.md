---
title: 'Contrôles ActiveX MFC : Ajout de méthodes personnalisées | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f0d52f3dec2967cc7a8d859e1f6845fe93c6fd6
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534883"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Contrôles ActiveX MFC : ajout de méthodes personnalisées
Méthodes personnalisées la différence des méthodes stock qu’ils ne sont pas déjà implémentées par `COleControl`. Vous devez fournir l’implémentation pour chaque méthode personnalisée que vous ajoutez à votre contrôle.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent les ActiveX, consultez [contrôles ActiveX](activex-controls.md).  
  
 Un utilisateur du contrôle ActiveX peut appeler une méthode personnalisée à tout moment pour effectuer des actions spécifiques du contrôle. L’entrée de mappage de répartition pour les méthodes personnalisées est au format DISP_FUNCTION.  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a> Ajout d’une méthode personnalisée avec l’Assistant Ajout de méthode  
 La procédure suivante illustre l’ajout de la méthode personnalisée PtInCircle au code de squelette d’un contrôle ActiveX. PtInCircle détermine si les coordonnées passées au contrôle sont à l’intérieur ou à l’extérieur du cercle. Cette procédure peut également être utilisée pour ajouter d’autres méthodes personnalisées. Remplacez par le nom de votre méthode personnalisée et ses paramètres pour le nom de la méthode PtInCircle et les paramètres.  
  
> [!NOTE]
>  Cet exemple utilise le `InCircle` fonction à partir de l’article événements. Pour plus d’informations sur cette fonction, consultez l’article [contrôles ActiveX MFC : ajout d’événements personnalisés à un contrôle ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).  
  
#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Pour ajouter la méthode personnalisée PtInCircle à l’aide de l’Assistant Ajout de méthode  
  
1.  Charger le projet du contrôle.  
  
2.  Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.  
  
3.  Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.  
  
4.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une méthode**.  
  
     Cette opération ouvre l’Assistant Ajout de méthode.  
  
5.  Dans le **nom de la méthode** , tapez *PtInCircle*.  
  
6.  Dans le **nom interne** , tapez le nom de fonction interne de la méthode ou la valeur par défaut (dans ce cas, *PtInCircle*).  
  
7.  Dans le **Type de retour** , cliquez sur **VARIANT_BOOL** pour le type de retour de la méthode.  
  
8.  À l’aide de la **Type de paramètre** et **nom du paramètre** contrôles, ajoutez un paramètre appelé *xCoord* (type *OLE_XPOS_PIXELS*).  
  
9. À l’aide de la **Type de paramètre** et **nom du paramètre** contrôles, ajoutez un paramètre appelé *yCoord* (type *OLE_YPOS_PIXELS*).  
  
10. Cliquez sur **Terminer**.  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a> Ajouter la méthode Assistant change pour les méthodes personnalisées  
 Lorsque vous ajoutez une méthode personnalisée, l’Assistant Ajout de méthode apporte des modifications à l’en-tête de classe de contrôle (. (H) et d’implémentation (. Fichiers CPP). La ligne suivante est ajoutée à la déclaration de carte de répartition dans l’en-tête de classe de contrôle (. H) fichier :  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 Ce code déclare un gestionnaire de méthode de distribution appelé `PtInCircle`. Cette fonction peut être appelée par l’utilisateur du contrôle en utilisant le nom externe `PtInCircle`.  
  
 La ligne suivante est ajoutée pour le contrôle. Fichier IDL :  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 Cette ligne assigne le `PtInCircle` un numéro d’identification spécifique (méthode), la position dans la liste de méthodes et propriétés Assistant Ajout de méthode. Étant donné que l’Assistant Ajout de méthode a été utilisé pour ajouter la méthode personnalisée, l’entrée correspondante a été ajoutée automatiquement pour le projet. Fichier IDL.  
  
 En outre, la ligne suivante, situé dans l’implémentation (. Fichier CPP) de la classe de contrôle, est ajouté à la table de dispatch du contrôle :  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 La macro DISP_FUNCTION mappe la méthode `PtInCircle` à fonction de gestionnaire du contrôle, `PtInCircle`, déclare le type de retour soit **VARIANT_BOOL**et déclare deux paramètres de type **VTS_XPOS_PIXELS** et **VTS_YPOSPIXELS** à passer à `PtInCircle`.  
  
 Enfin, l’Assistant Ajout de méthode ajoute la fonction stub `CSampleCtrl::PtInCircle` vers le bas de l’implémentation du contrôle (. Fichier CPP). Pour `PtInCircle` pour fonctionner comme indiqué précédemment, il doit être modifié comme suit :  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Affichage de classes et Explorateur d’objets, icônes](/visualstudio/ide/class-view-and-object-browser-icons)

