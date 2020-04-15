---
title: 'Contrôles ActiveX MFC : ajout de méthodes personnalisées'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 88d486248eab5d980463764db34bf40b05b830dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364714"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Contrôles ActiveX MFC : ajout de méthodes personnalisées

Les méthodes personnalisées diffèrent des méthodes de `COleControl`stock en ce qu’elles ne sont pas déjà mises en œuvre par . Vous devez fournir la mise en œuvre pour chaque méthode personnalisée que vous ajoutez à votre contrôle.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Un utilisateur de contrôle ActiveX peut appeler une méthode personnalisée à tout moment pour effectuer des actions spécifiques au contrôle. L’entrée de carte de répartition pour les méthodes personnalisées est du formulaire DISP_FUNCTION.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Ajout d’une méthode personnalisée avec le Magicien de la méthode Add

La procédure suivante démontre l’ajout de la méthode personnalisée PtInCircle au code squelette d’un contrôle ActiveX. PtInCircle détermine si les coordonnées passées au contrôle sont à l’intérieur ou à l’extérieur du cercle. Cette même procédure peut également être utilisée pour ajouter d’autres méthodes personnalisées. Remplacez votre nom de méthode personnalisé et ses paramètres par le nom et les paramètres de la méthode PtInCircle.

> [!NOTE]
> Cet exemple `InCircle` utilise la fonction de l’article Événements. Pour plus d’informations sur cette fonction, voir l’article [MFC ActiveX Controls: Adding Custom Events à un contrôle ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Pour ajouter la méthode personnalisée PtInCircle à l’aide de l’Add Method Wizard

1. Chargez le projet du contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite ajouter **la méthode**.

   Cela ouvre le Assistant Méthode Add.

1. Dans la boîte **de nom de méthode,** tapez *PtInCircle*.

1. Dans la boîte **de nom interne,** tapez le nom de la fonction interne de la méthode ou utilisez la valeur par défaut (dans ce cas, *PtInCircle*).

1. Dans la boîte **de type retour,** cliquez **sur VARIANT_BOOL** pour le type de retour de la méthode.

1. À l’aide des contrôles **de type de paramètre** et **de nom de paramètre,** ajoutez un paramètre appelé *xCoord* (type *OLE_XPOS_PIXELS*).

1. À l’aide des contrôles **de type de paramètre** et **de nom de paramètre,** ajoutez un paramètre appelé *yCoord* (type *OLE_YPOS_PIXELS*).

1. Cliquez sur **Terminer**.

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Ajouter des modifications de magicien de méthode pour des méthodes personnalisées

Lorsque vous ajoutez une méthode personnalisée, le Add Method Wizard apporte quelques modifications à l’en-tête de la classe de contrôle (. H) et la mise en œuvre (. dossiers du RPC). La ligne suivante est ajoutée à la déclaration de carte de répartition dans l’en-tête de classe de contrôle (. H) fichier:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Ce code déclare un gestionnaire `PtInCircle`de méthode de répartition appelé . Cette fonction peut être appelée par l’utilisateur de contrôle en utilisant le nom `PtInCircle`externe .

La ligne suivante est ajoutée à la ligne de contrôle . Fichier IDL:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Cette ligne attribue `PtInCircle` à la méthode un numéro d’identification spécifique, la position de la méthode dans la liste des méthodes et des propriétés Add Method Wizard. Parce que le Magicien De méthode Add a été utilisé pour ajouter la méthode personnalisée, l’entrée pour elle a été ajoutée automatiquement à la . Fichier IDL.

En outre, la ligne suivante, située dans la mise en œuvre (. Le fichier du RPC de la classe de contrôle est ajouté à la carte de répartition du contrôle :

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

Le DISP_FUNCTION macro cartes `PtInCircle` de la méthode à `PtInCircle`la fonction de gestionnaire du contrôle, , déclare le type de retour d’être **VARIANT_BOOL**, `PtInCircle`et déclare deux paramètres de type **VTS_XPOS_PIXELS** et **VTS_YPOSPIXELS** à passer à .

Enfin, le Add Method Wizard `CSampleCtrl::PtInCircle` ajoute la fonction de talon au bas de la mise en œuvre du contrôle (. dossier du RPC. Pour `PtInCircle` fonctionner comme indiqué précédemment, il doit être modifié comme suit :

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Icônes de navigateur de vue de classe et d’objet](/visualstudio/ide/class-view-and-object-browser-icons)
