---
title: Implémentation des Pages de propriétés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1db6ca4ea374cd76d5b0e1df8e6c0cd03474fdf2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357491"
---
# <a name="implementing-property-pages"></a>Implémentation des Pages de propriétés
Pages de propriétés sont des objets COM qui implémentent la `IPropertyPage` ou **IPropertyPage2** interface. ATL fournit la prise en charge pour l’implémentation des pages de propriétés par le biais du [Assistant Page de propriétés ATL](../atl/reference/atl-property-page-wizard.md) dans les [boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md).  
  
 Pour créer une page de propriétés ATL à l’aide de :  
  
-   Créez ou ouvrez un projet de serveur ATL Dynamic-link library (DLL).  
  
-   Ouvrez le [boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md) et sélectionnez **Page de propriétés ATL**.  
  
-   Assurez-vous que votre page de propriétés est cloisonnés (puisqu’elle a une interface utilisateur).  
  
-   Définir le titre, la description (Doc String) et le fichier d’aide à associer à votre page.  
  
-   Ajouter des contrôles à la ressource de boîte de dialogue générée en tant que l’interface utilisateur de votre page de propriétés.  
  
-   Répondre aux modifications dans l’interface utilisateur de votre page pour effectuer la validation, de mettre à jour le site de la page ou de mettre à jour les objets associés à votre page. En particulier, appelez [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) lorsque l’utilisateur apporte des modifications à la page de propriétés.  
  
-   Si vous le souhaitez remplacer le `IPropertyPageImpl` méthodes en utilisant les instructions ci-dessous.  
  
    |Méthode IPropertyPageImpl|Remplacer lorsque vous souhaitez...|Notes|  
    |------------------------------|----------------------------------|-----------|  
    |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Effectuer les vérifications de validité de base sur le nombre d’objets passés à votre page et les interfaces prises en charge.|Exécutez votre propre code avant d’appeler l’implémentation de classe de base. Si les objets en cours de définition ne sont pas conformes à vos attentes, vous devez échouer l’appel dès que possible.|  
    |[Activer](../atl/reference/ipropertypageimpl-class.md#activate)|Initialiser l’interface utilisateur de votre page (par exemple, définir des contrôles de boîte de dialogue avec les valeurs de propriété actuelles à partir des objets, créez des contrôles dynamiquement ou effectuer d’autres initialisations).|Appeler l’implémentation de classe de base avant votre code afin que la classe de base a la possibilité de créer la fenêtre de dialogue et tous les contrôles avant d’essayer de les mettre à jour.|  
    |[appliquer](../atl/reference/ipropertypageimpl-class.md#apply)|Vérifiez les paramètres de propriété et mettre à jour les objets.|Il n’est pas nécessaire d’appeler l’implémentation de classe de base, car il ne fait rien en dehors de la trace de l’appel.|  
    |[Désactiver](../atl/reference/ipropertypageimpl-class.md#deactivate)|Nettoyer les éléments relatifs à la fenêtre.|L’implémentation de classe de base détruit la boîte de dialogue représentant la page de propriétés. Si vous avez besoin nettoyer avant la destruction de la boîte de dialogue, vous devez ajouter le code avant d’appeler la classe de base.|  
  
 Pour un exemple d’implémentation de page de propriété, consultez [exemple : implémentation d’une Page de propriétés](../atl/example-implementing-a-property-page.md).  
  
> [!NOTE]
>  Si vous souhaitez héberger des contrôles ActiveX dans votre page de propriétés, vous devez modifier la dérivation de la classe générée par l’Assistant. Remplacez **CDialogImpl\<CYourClass >** avec **CAxDialogImpl\<CYourClass >** dans la liste des classes de base.  
  
## <a name="see-also"></a>Voir aussi  
 [Pages de propriétés](../atl/atl-com-property-pages.md)   
 [Exemple ATLPages](../visual-cpp-samples.md)

