---
title: Pages de propriétés ATL COM
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
ms.openlocfilehash: d374569c6c3e9bb63b6b026d2b0f86226d158f36
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768407"
---
# <a name="atl-com-property-pages"></a>Pages de propriétés ATL COM

Pages de propriétés COM fournissent une interface utilisateur pour définir les propriétés (ou en appelant les méthodes) d’un ou plusieurs objets COM. Pages de propriétés sont largement utilisées par les contrôles ActiveX pour fournir des interfaces utilisateur riches qui permettent des propriétés de contrôle au moment du design.

Pages de propriétés sont des objets COM qui implémentent le [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) ou [IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) interface. Ces interfaces fournissent des méthodes qui permettent à associer à la page une `site` (un objet COM qui représente le conteneur de la page) et un nombre de *objets* (objets COM dont les méthodes sont appelées en réponse aux modifications effectuées par l’utilisateur de la page de propriétés). Le conteneur de page de propriété est chargé d’appeler des méthodes sur l’interface de page de propriété pour indiquer la page pour afficher ou masquer son interface utilisateur et quand appliquer les modifications apportées par l’utilisateur pour les objets sous-jacents.

Chaque page de propriétés peut être généré complètement indépendamment les objets dont les propriétés peuvent être définies. Une page de propriétés a besoin que pour comprendre une interface particulière (ou un ensemble d’interfaces) et pour fournir une interface utilisateur pour appeler les méthodes sur cette interface.

Pour plus d’informations, consultez [feuilles de propriétés et Pages de propriétés](/windows/desktop/com/property-sheets-and-property-pages) dans le SDK Windows.

## <a name="in-this-section"></a>Dans cette section

[Spécification des pages de propriétés](../atl/specifying-property-pages.md)<br/>
Répertorie les étapes permettant de spécifier les pages de propriétés de votre contrôle et montre un exemple de classe.

[Implémentation de pages de propriétés](../atl/implementing-property-pages.md)<br/>
Répertorie les étapes d’implémentation des pages de propriétés, y compris les méthodes à substituer. Vous présente un exemple complet en fonction de l’exemple de programme ATLPages.

## <a name="related-sections"></a>Rubriques connexes

[Exemple ATLPages](../overview/visual-cpp-samples.md)<br/>
Extrait de l’exemple ATLPages, qui implémente une page de propriété à l’aide de `IPropertyPageImpl`.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)
