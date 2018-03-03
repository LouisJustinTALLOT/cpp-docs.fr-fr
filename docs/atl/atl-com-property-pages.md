---
title: "Pages de propriétés de COM ATL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08b1c31aeaba25f4eadad5225dd2f5607cf7053c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="atl-com-property-pages"></a>Pages de propriétés ATL COM
Pages de propriétés COM fournissent une interface utilisateur pour définir les propriétés (ou en appelant les méthodes) d’un ou plusieurs objets COM. Pages de propriétés sont largement utilisées par les contrôles ActiveX pour fournir des interfaces utilisateur riches qui permettent le contrôle des propriétés au moment du design.  
  
 Pages de propriétés sont des objets COM qui implémentent la [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) ou [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) interface. Ces interfaces fournissent des méthodes qui permettent à la page à associer à un `site` (un objet COM qui représente le conteneur de la page) et un nombre de *objets* (objets COM dont les méthodes sont appelées en réponse aux modifications effectuées par l’utilisateur de la page de propriétés). Le conteneur de page de propriété est chargé d’appeler des méthodes sur l’interface de page de propriété pour indiquer la page pour afficher ou masquer son interface utilisateur et le moment d’appliquer les modifications apportées par l’utilisateur pour les objets sous-jacents.  
  
 Chaque page de propriétés peut être construite entièrement indépendamment les objets dont les propriétés peuvent être définies. Une page de propriétés a besoin qu’à comprendre une interface particulière (ou un ensemble d’interfaces) et pour fournir une interface utilisateur pour appeler les méthodes de cette interface.  
  
 Pour plus d’informations, consultez [feuilles de propriétés et Pages de propriétés](http://msdn.microsoft.com/library/windows/desktop/ms686577) dans le [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Spécification des pages de propriétés](../atl/specifying-property-pages.md)  
 Répertorie les étapes permettant de spécifier les pages de propriétés de votre contrôle et montre un exemple de classe.  
  
 [Implémentation de pages de propriétés](../atl/implementing-property-pages.md)  
 Répertorie les étapes d’implémentation des pages de propriétés, y compris les méthodes à substituer. Vous guide pour obtenir un exemple complet basé sur l’exemple de programme ATLPages.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Exemple ATLPages](../visual-cpp-samples.md)  
 Extrait de l’exemple ATLPages, qui implémente une page de propriété à l’aide de `IPropertyPageImpl`.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)

