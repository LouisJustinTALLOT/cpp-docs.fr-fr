---
description: 'En savoir plus sur : utilisation des feuilles de propriétés dans votre application'
title: Utilisation des feuilles de propriétés dans votre application
ms.date: 11/04/2016
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
ms.openlocfilehash: 3bc1e21d99eb4a1688247524749b44028762892d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322684"
---
# <a name="using-property-sheets-in-your-application"></a>Utilisation des feuilles de propriétés dans votre application

Pour utiliser une feuille de propriétés dans votre application, procédez comme suit :

1. Créez une ressource modèle de boîte de dialogue dans chaque page de propriétés. N'oubliez pas que l'utilisateur peut basculer d'une page à l'autre, donc la présentation de chaque page doit être aussi cohérente que possible.

   Les modèles de boîte de dialogue pour toutes les pages ne doivent pas nécessairement avoir la même taille. Le framework utilise la taille de la plus grande page pour déterminer la quantité d'espace à allouer dans la feuille de propriétés pour les pages de propriétés.

   Lorsque vous créez la ressource modèle de la boîte de dialogue pour une page de propriétés, vous devez spécifier les styles suivants dans la feuille de propriétés Propriétés de la boîte dialogue :

   - Définissez la zone d’édition de la **légende** de la page **général** sur le texte que vous souhaitez voir apparaître dans l’onglet de cette page.

   - Affectez la valeur **enfant** à la zone de liste **style** de la page **styles** .

   - Affectez à la zone de liste **bordure** de la page **styles** la valeur **fin**.

   - Vérifiez que la case à cocher de la zone de **titre** de la page **styles** est activée.

   - Vérifiez que la case à cocher **désactivé** de la page **plus de styles** est sélectionnée.

1. Créez une classe dérivée de [CPropertyPage](../mfc/reference/cpropertypage-class.md)correspondant à chaque modèle de boîte de dialogue de page de propriétés. Consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md). Choisissez `CPropertyPage` en tant que classe de base.

1. Créez des variables membres pour contenir les valeurs de cette page de propriétés. Le processus d'ajout des variables membres à une page de propriétés est identique au processus d'ajout des variables membres à une boîte de dialogue, car une page de propriétés est une boîte de dialogue spécialisée. Pour plus d’informations, consultez [définition de variables membres pour les contrôles de boîte de dialogue](../windows/adding-editing-or-deleting-controls.md).

1. Construisez un objet [CPropertySheet](../mfc/reference/cpropertysheet-class.md) dans votre code source. Généralement, vous construisez l'objet `CPropertySheet` dans le gestionnaire de la commande qui affiche la feuille de propriétés. Cet objet représente la feuille de propriétés entière. Si vous créez une feuille de propriétés modale avec la fonction [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) , le Framework fournit trois boutons de commande par défaut : OK, annuler et appliquer. L’infrastructure ne crée aucun bouton de commande pour les feuilles de propriétés non modales créées avec la fonction [Create](../mfc/reference/cpropertysheet-class.md#create) . Vous n'avez pas besoin de dériver une classe `CPropertySheet` à moins de vouloir ajouter d'autres contrôles (comme une fenêtre d'aperçu) ou afficher une feuille de propriétés non modales. Cette étape est nécessaire pour les feuilles de propriétés non modales car elles ne contiennent aucun contrôle par défaut qui peut être utilisé pour fermer la feuille de propriétés.

1. Pour chaque page à ajouter à la feuille de propriétés, procédez comme suit :

   - Construisez un objet pour chaque classe dérivée `CPropertyPage` que vous avez créée précédemment pendant ce processus.

   - Appelez [CPropertySheet :: AddPage](../mfc/reference/cpropertysheet-class.md#addpage) pour chaque page.

   En général, l'objet qui crée `CPropertySheet` crée également les objets `CPropertyPage` de cette étape. Toutefois, si vous implémentez une classe dérivée de `CPropertySheet`, vous pouvez inclure des objets `CPropertyPage` dans l'objet `CPropertySheet` et appeler `AddPage` pour chaque page du constructeur de classe dérivée de `CPropertySheet`. `AddPage` ajoute l'objet `CPropertyPage` à la liste de pages de la feuille de propriétés mais ne crée pas réellement la fenêtre de cette page. Par conséquent, il n'est pas nécessaire d'attendre jusqu'à la conception de la fenêtre de la feuille de propriétés pour appeler `AddPage` ; vous pouvez appeler `AddPage` du constructeur de la feuille de propriétés.

   Par défaut, si une feuille de propriétés contient plus d'onglets que ceux qui tiennent sur une ligne de la feuille de propriétés, les onglets s'empileront sur plusieurs lignes. Pour désactiver l’empilement, appelez [CPropertySheet :: EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) avec le paramètre défini sur **false**. Vous devez appeler `EnableStackedTabs` lorsque vous créez la feuille de propriétés.

1. Appelez [CPropertySheet ::D omodal](../mfc/reference/cpropertysheet-class.md#domodal) ou [Create](../mfc/reference/cpropertysheet-class.md#create) pour afficher la feuille de propriétés. Appelez `DoModal` pour créer une feuille de propriétés comme une boîte de dialogue modale. Appelez **Create** pour créer la feuille de propriétés en tant que boîte de dialogue non modale.

1. Échangez des données entre les pages de propriétés et le propriétaire de la feuille de propriétés. Cela est expliqué dans l’article [échange de données](../mfc/exchanging-data.md).

Pour obtenir un exemple d’utilisation des feuilles de propriétés, consultez l’exemple général MFC [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](../mfc/property-sheets-mfc.md)
