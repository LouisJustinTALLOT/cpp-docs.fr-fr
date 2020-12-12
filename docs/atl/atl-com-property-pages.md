---
description: En savoir plus sur les pages de propriétés ATL COM
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
ms.openlocfilehash: 252e8a98f4f34a07a374c77fc48aacd7eee8969f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165977"
---
# <a name="atl-com-property-pages"></a>Pages de propriétés ATL COM

Les pages de propriétés COM fournissent une interface utilisateur permettant de définir les propriétés (ou d’appeler les méthodes) d’un ou plusieurs objets COM. Les pages de propriétés sont largement utilisées par les contrôles ActiveX pour fournir des interfaces utilisateur riches qui permettent de définir les propriétés de contrôle au moment de la conception.

Les pages de propriétés sont des objets COM qui implémentent l’interface [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) ou [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) . Ces interfaces fournissent des méthodes qui permettent à la page d’être associée à un `site` (un objet com représentant le conteneur de la page) et à un certain nombre d' *objets* (objets com dont les méthodes sont appelées en réponse à des modifications apportées par l’utilisateur de la page de propriétés). Le conteneur de la page de propriétés est chargé d’appeler des méthodes sur l’interface de la page de propriétés pour indiquer à la page quand afficher ou masquer son interface utilisateur, et quand appliquer les modifications apportées par l’utilisateur aux objets sous-jacents.

Chaque page de propriétés peut être construite entièrement indépendamment des objets dont les propriétés peuvent être définies. Tout ce dont a besoin une page de propriétés consiste à comprendre une interface particulière (ou un ensemble d’interfaces) et à fournir une interface utilisateur pour appeler des méthodes sur cette interface.

Pour plus d’informations, consultez [feuilles de propriétés et pages de propriétés](/windows/win32/com/property-sheets-and-property-pages) dans le SDK Windows.

## <a name="in-this-section"></a>Dans cette section

[Spécification des pages de propriétés](../atl/specifying-property-pages.md)<br/>
Répertorie les étapes de spécification des pages de propriétés pour votre contrôle et montre un exemple de classe.

[Implémentation des pages de propriétés](../atl/implementing-property-pages.md)<br/>
Répertorie les étapes d’implémentation des pages de propriétés, y compris les méthodes à substituer. Vous guide tout au long d’un exemple complet basé sur l’exemple de programme ATLPages.

## <a name="related-sections"></a>Sections connexes

[Exemple ATLPages](../overview/visual-cpp-samples.md)<br/>
Exemple abstrait pour l’exemple ATLPages, qui implémente une page de propriétés à l’aide de `IPropertyPageImpl` .

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)
