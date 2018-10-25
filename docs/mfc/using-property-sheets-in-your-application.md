---
title: À l’aide de feuilles de propriétés dans votre Application | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc151ae25df4cac2c6b5ed9ac5a523efda28dff2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082708"
---
# <a name="using-property-sheets-in-your-application"></a>Utilisation des feuilles de propriétés dans votre application

Pour utiliser une feuille de propriétés dans votre application, procédez comme suit :

1. Créez une ressource modèle de boîte de dialogue dans chaque page de propriétés. N'oubliez pas que l'utilisateur peut basculer d'une page à l'autre, donc la présentation de chaque page doit être aussi cohérente que possible.

   Les modèles de boîte de dialogue pour toutes les pages ne doivent pas nécessairement avoir la même taille. Le framework utilise la taille de la plus grande page pour déterminer la quantité d'espace à allouer dans la feuille de propriétés pour les pages de propriétés.

   Lorsque vous créez la ressource modèle de la boîte de dialogue pour une page de propriétés, vous devez spécifier les styles suivants dans la feuille de propriétés Propriétés de la boîte dialogue :

   - Définir le **légende** zone d’édition sur le **général** page pour le texte que vous souhaitez voir s’afficher dans l’onglet de cette page.

   - Définir le **Style** zone de liste sur le **Styles** page à **enfant**.

   - Définir le **bordure** zone de liste sur le **Styles** page à **Thin**.

   - Vérifiez que le **Titlebar** case à cocher sur la **Styles** page est sélectionnée.

   - Vérifiez que le **désactivé** case à cocher sur la **plus de Styles** page est sélectionnée.

1. Créer un [CPropertyPage](../mfc/reference/cpropertypage-class.md)-correspondant à chaque modèle de boîte de dialogue de page de propriétés de classe dérivée. Consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md). Choisissez `CPropertyPage` en tant que classe de base.

1. Créez des variables membres pour contenir les valeurs de cette page de propriétés. Le processus d'ajout des variables membres à une page de propriétés est identique au processus d'ajout des variables membres à une boîte de dialogue, car une page de propriétés est une boîte de dialogue spécialisée. Pour plus d’informations, consultez [définition des Variables membres pour les contrôles de boîte de dialogue](../windows/defining-member-variables-for-dialog-controls.md).

1. Construire un [CPropertySheet](../mfc/reference/cpropertysheet-class.md) objet dans votre code source. Généralement, vous construisez l'objet `CPropertySheet` dans le gestionnaire de la commande qui affiche la feuille de propriétés. Cet objet représente la feuille de propriétés entière. Si vous créez une feuille de propriétés modale avec le [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) (fonction), le framework fournit trois boutons de commande par défaut : OK, Annuler et appliquer. L’infrastructure ne crée aucun bouton de commande pour les feuilles de propriétés non modales créées avec le [créer](../mfc/reference/cpropertysheet-class.md#create) (fonction). Vous n'avez pas besoin de dériver une classe `CPropertySheet` à moins de vouloir ajouter d'autres contrôles (comme une fenêtre d'aperçu) ou afficher une feuille de propriétés non modales. Cette étape est nécessaire pour les feuilles de propriétés non modales car elles ne contiennent aucun contrôle par défaut qui peut être utilisé pour fermer la feuille de propriétés.

1. Pour chaque page à ajouter à la feuille de propriétés, procédez comme suit :

   - Construisez un objet pour chaque classe dérivée `CPropertyPage` que vous avez créée précédemment pendant ce processus.

   - Appelez [CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage) pour chaque page.

   En général, l'objet qui crée `CPropertySheet` crée également les objets `CPropertyPage` de cette étape. Toutefois, si vous implémentez une classe dérivée de `CPropertySheet`, vous pouvez inclure des objets `CPropertyPage` dans l'objet `CPropertySheet` et appeler `AddPage` pour chaque page du constructeur de classe dérivée de `CPropertySheet`. `AddPage` ajoute l'objet `CPropertyPage` à la liste de pages de la feuille de propriétés mais ne crée pas réellement la fenêtre de cette page. Par conséquent, il n'est pas nécessaire d'attendre jusqu'à la conception de la fenêtre de la feuille de propriétés pour appeler `AddPage` ; vous pouvez appeler `AddPage` du constructeur de la feuille de propriétés.

   Par défaut, si une feuille de propriétés contient plus d'onglets que ceux qui tiennent sur une ligne de la feuille de propriétés, les onglets s'empileront sur plusieurs lignes. Pour désactiver l’empilement, appelez [CPropertySheet::EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) avec le paramètre défini sur **FALSE**. Vous devez appeler `EnableStackedTabs` lorsque vous créez la feuille de propriétés.

1. Appelez [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) ou [créer](../mfc/reference/cpropertysheet-class.md#create) pour afficher la feuille de propriétés. Appelez `DoModal` pour créer une feuille de propriétés comme une boîte de dialogue modale. Appelez **créer** pour créer la feuille de propriétés comme une boîte de dialogue non modale.

1. Échangez des données entre les pages de propriétés et le propriétaire de la feuille de propriétés. Cela est expliqué dans l’article [échange de données](../mfc/exchanging-data.md).

Pour obtenir un exemple montrant comment utiliser les feuilles de propriétés, consultez l’exemple général MFC [PROPDLG](../visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](../mfc/property-sheets-mfc.md)

