---
description: 'En savoir plus sur : implémentation des pages de propriétés'
title: Implémentation de pages de propriétés
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: 5f05831fa23eff586e85db56eca8013e0d1d2ea2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147756"
---
# <a name="implementing-property-pages"></a>Implémentation de pages de propriétés

::: moniker range="msvc-160"

L’Assistant Page de propriétés ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=msvc-150"

Les pages de propriétés sont des objets COM qui implémentent l’interface `IPropertyPage` ou `IPropertyPage2`. ATL prend en charge l’implémentation de pages de propriétés via l’[Assistant Page de propriétés ATL](../atl/reference/atl-property-page-wizard.md) dans la [boîte de dialogue Ajouter une classe](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box).

Pour créer une page de propriétés à l’aide d’ATL :

- Créez ou ouvrez un projet de serveur de bibliothèque de liens dynamiques (DLL) ATL.

- Ouvrez la [boîte de dialogue Ajouter une classe](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) et sélectionnez **Page de propriétés ATL**.

- Assurez-vous que votre page de propriétés est cloisonnée (puisqu’elle a une interface utilisateur).

- Configurez le titre, la description (Chaîne Doc) et le fichier d’aide à associer à votre page.

- Ajoutez les contrôles à la ressource boîte de dialogue générée pour faire office d’interface utilisateur de votre page de propriétés.

- Répondez aux modifications apportées dans l’interface utilisateur de votre page pour effectuer la validation, mettre à jour le site de la page ou mettre à jour les objets associés à votre page. En particulier, appelez [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) lorsque l’utilisateur apporte des modifications à la page de propriétés.

- Si vous le souhaitez, remplacez les méthodes `IPropertyPageImpl` en suivant les recommandations ci-dessous.

   |Méthode IPropertyPageImpl|Si vous souhaitez...|Remarques|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Effectuer des vérifications de validité de base sur le nombre d’objets passés à votre page et les interfaces prises en charge.|Exécuter votre propre code avant d’appeler l’implémentation de classe de base. Si les objets en cours de définition ne sont pas conformes à vos attentes, vous devez terminer l’appel dès que possible.|
   |[Activer](../atl/reference/ipropertypageimpl-class.md#activate)|Initialiser l’interface utilisateur de votre page (par exemple, définir des contrôles de boîte de dialogue avec les valeurs de propriété actuelles des objets, créer des contrôles dynamiquement ou effectuer d’autres initialisations).|Appeler l’implémentation de classe de base avant votre code afin que la classe de base ait la possibilité de créer une fenêtre de dialogue et tous les contrôles avant que vous essayiez de les mettre à jour.|
   |[Appliquer](../atl/reference/ipropertypageimpl-class.md#apply)|Valider les paramètres de propriété et mettre à jour les objets.|Il est inutile d’appeler l’implémentation de classe de base dans la mesure où elle ne fait que tracer l’appel.|
   |[Désactivation](../atl/reference/ipropertypageimpl-class.md#deactivate)|Nettoyer les éléments liés aux fenêtres.|L’implémentation de classe de base détruit la boîte de dialogue représentant la page de propriétés. Si vous avez besoin de nettoyer avant la destruction de la boîte de dialogue, vous devez ajouter votre code avant d’appeler la classe de base.|

Pour obtenir un exemple d’implémentation de page de propriétés, consultez [exemple : implémentation d’une page de propriétés](../atl/example-implementing-a-property-page.md).

> [!NOTE]
> Si vous souhaitez héberger des contrôles ActiveX dans votre page de propriétés, vous devez modifier la dérivation de votre classe générée par l’Assistant. Remplacez **CDialogImpl \<CYourClass>** par **CAxDialogImpl \<CYourClass>** dans la liste des classes de base.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../atl/atl-com-property-pages.md)<br/>
[Exemple ATLPages](../overview/visual-cpp-samples.md)
