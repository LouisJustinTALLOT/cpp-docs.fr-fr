---
title: Implémentation des Pages de propriétés
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: 8999f6469e420fa86cb1267675f10dc173d45ff0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776246"
---
# <a name="implementing-property-pages"></a>Implémentation des Pages de propriétés

Pages de propriétés sont des objets COM qui implémentent le `IPropertyPage` ou `IPropertyPage2` interface. ATL fournit la prise en charge pour l’implémentation de pages de propriétés via la [Assistant Page de propriétés ATL](../atl/reference/atl-property-page-wizard.md) dans le [boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md).

Pour créer une page de propriétés à l’aide d’ATL :

- Créez ou ouvrez un projet de serveur de bibliothèque (DLL) de DLL ATL.

- Ouvrez le [boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md) et sélectionnez **Page de propriétés ATL**.

- Assurez-vous que votre page de propriétés est cloisonnés (puisqu’elle a une interface utilisateur).

- Définir le titre, la description (Chaîne Doc) et le fichier d’aide à associer à votre page.

- Ajouter des contrôles à la ressource de boîte de dialogue généré en tant que l’interface utilisateur de votre page de propriétés.

- Répondre aux modifications apportées dans l’interface utilisateur de votre page pour effectuer la validation, mettre à jour le site de la page ou mettre à jour les objets associés à votre page. En particulier, appelez [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) lorsque l’utilisateur apporte des modifications à la page de propriétés.

- Si vous le souhaitez remplacer le `IPropertyPageImpl` méthodes en suivant les recommandations ci-dessous.

   |Méthode IPropertyPageImpl|Substituer lorsque vous souhaitez...|Notes|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Effectuer des vérifications de validité de base sur le nombre d’objets passés à votre page et les interfaces qui prennent en charge.|Exécuter votre propre code avant d’appeler l’implémentation de classe de base. Si les objets en cours de définition non conformes à vos attentes, vous devez échouer l’appel dès que possible.|
   |[Activer](../atl/reference/ipropertypageimpl-class.md#activate)|Initialiser l’interface utilisateur de votre page (par exemple, définir des contrôles de boîte de dialogue avec les valeurs de propriété actuelles à partir d’objets, créer dynamiquement des contrôles ou effectuer d’autres initialisations).|Appeler l’implémentation de classe de base avant votre code afin que la classe de base a la possibilité de créer la fenêtre de la boîte de dialogue et tous les contrôles avant d’essayer de les mettre à jour.|
   |[Appliquer](../atl/reference/ipropertypageimpl-class.md#apply)|Valider les paramètres de propriété et mettre à jour les objets.|Il est inutile d’appeler l’implémentation de classe de base dans la mesure où il ne fait rien en dehors de la trace de l’appel.|
   |[Deactivate](../atl/reference/ipropertypageimpl-class.md#deactivate)|Nettoyer les éléments liés aux fenêtres.|L’implémentation de classe de base détruit la boîte de dialogue représentant la page de propriétés. Si vous avez besoin nettoyer avant la destruction de la boîte de dialogue, vous devez ajouter votre code avant d’appeler la classe de base.|

Pour un exemple d’implémentation de page de propriété, consultez [exemple : Implémentation d’une Page de propriété](../atl/example-implementing-a-property-page.md).

> [!NOTE]
> Si vous souhaitez héberger des contrôles ActiveX dans votre page de propriétés, vous devez modifier la dérivation de votre classe générées par l’Assistant. Remplacez **CDialogImpl\<CYourClass >** avec **CAxDialogImpl\<CYourClass >** dans la liste des classes de base.

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../atl/atl-com-property-pages.md)<br/>
[Exemple ATLPages](../overview/visual-cpp-samples.md)
