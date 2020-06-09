---
title: 'Contrôles ActiveX MFC : ajout de méthodes personnalisées'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: e32a1c372d89fc4ade414b20a0f77fa162807250
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626158"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Contrôles ActiveX MFC : ajout de méthodes personnalisées

Les méthodes personnalisées diffèrent des méthodes stock en ce qu’elles ne sont pas encore implémentées par `COleControl` . Vous devez fournir l’implémentation pour chaque méthode personnalisée que vous ajoutez à votre contrôle.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Un utilisateur de contrôle ActiveX peut appeler une méthode personnalisée à tout moment pour effectuer des actions spécifiques au contrôle. L’entrée de la table de dispatch pour les méthodes personnalisées se présente sous la forme DISP_FUNCTION.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Ajout d’une méthode personnalisée avec l’Assistant Ajout de méthode

La procédure suivante montre comment ajouter la méthode personnalisée PtInCircle au code squelette d’un contrôle ActiveX. PtInCircle détermine si les coordonnées passées au contrôle se trouvent à l’intérieur ou à l’extérieur du cercle. Cette même procédure peut également être utilisée pour ajouter d’autres méthodes personnalisées. Remplacez le nom et les paramètres de la méthode PtInCircle par le nom de votre méthode personnalisée et ses paramètres.

> [!NOTE]
> Cet exemple utilise la `InCircle` fonction de l’article événements. Pour plus d’informations sur cette fonction, consultez l’article [contrôles ActiveX MFC : ajout d’événements personnalisés à un contrôle ActiveX](mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Pour ajouter la méthode personnalisée PtInCircle à l’aide de l’Assistant Ajout de méthode

1. Chargez le projet du contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une méthode**.

   L’Assistant Ajout de méthode s’ouvre.

1. Dans la zone nom de la **méthode** , tapez *PtInCircle*.

1. Dans la zone **nom interne** , tapez le nom de la fonction interne de la méthode ou utilisez la valeur par défaut (dans ce cas, *PtInCircle*).

1. Dans la zone **type de retour** , cliquez sur **VARIANT_BOOL** pour le type de retour de la méthode.

1. À l’aide des contrôles de **type de paramètre** et de **nom de paramètre** , ajoutez un paramètre appelé *xCoord* (type *OLE_XPOS_PIXELS*).

1. À l’aide des contrôles de **type de paramètre** et de **nom de paramètre** , ajoutez un paramètre appelé *yCoord* (type *OLE_YPOS_PIXELS*).

1. Cliquez sur **Terminer**.

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Modifications de l’Assistant Ajout de méthode pour les méthodes personnalisées

Lorsque vous ajoutez une méthode personnalisée, l’Assistant Ajout de méthode apporte certaines modifications à l’en-tête de la classe du contrôle (. H) et l’implémentation (. CPP). La ligne suivante est ajoutée à la déclaration de la table de dispatch dans l’en-tête de la classe du contrôle (. H) :

[!code-cpp[NVC_MFC_AxUI#18](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Ce code déclare un gestionnaire de méthode de distribution appelé `PtInCircle` . Cette fonction peut être appelée par l’utilisateur du contrôle à l’aide du nom externe `PtInCircle` .

La ligne suivante est ajoutée au du contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxUI#19](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Cette ligne affecte à la `PtInCircle` méthode un numéro d’identification spécifique, la position de la méthode dans la liste des méthodes et propriétés de l’Assistant Ajout d’une méthode. Étant donné que l’Assistant Ajout de méthode a été utilisé pour ajouter la méthode personnalisée, l’entrée correspondante a été ajoutée automatiquement au du projet. Fichier IDL.

En outre, la ligne suivante, située dans l’implémentation (. CPP) de la classe de contrôle, est ajouté à la table de dispatch du contrôle :

[!code-cpp[NVC_MFC_AxUI#20](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

La macro DISP_FUNCTION mappe la méthode `PtInCircle` à la fonction de gestionnaire du contrôle, `PtInCircle` , déclare le type de retour à **VARIANT_BOOL**et déclare deux paramètres de type **VTS_XPOS_PIXELS** et **VTS_YPOSPIXELS** à passer à `PtInCircle` .

Enfin, l’Assistant Ajout de méthode ajoute la fonction stub `CSampleCtrl::PtInCircle` au bas de l’implémentation du contrôle (. CPP). Pour `PtInCircle` qu’elle fonctionne comme indiqué précédemment, elle doit être modifiée comme suit :

[!code-cpp[NVC_MFC_AxUI#21](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Icônes de l’Explorateur d’objets et de Affichage de classes](/visualstudio/ide/class-view-and-object-browser-icons)
