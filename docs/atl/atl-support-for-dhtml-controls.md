---
title: Prise en charge ATL pour les contrôles DHTML | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5144a11f0b035822e6f729692569e5e861c44dcc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758308"
---
# <a name="atl-support-for-dhtml-controls"></a>Prise en charge ATL pour les contrôles DHTML

À l’aide d’ATL, vous pouvez créer un contrôle avec la fonctionnalité de DHTML (Dynamic HTML). Un contrôle ATL DHTML :

- Héberge le contrôle WebBrowser.

- Spécifie, à l’aide de HTML, l’interface utilisateur (IU) du contrôle DHTML Edit.

- Accède à l’objet WebBrowser et ses méthodes via son interface, [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx).

- Gère la communication entre le code C++ et HTML.

Un contrôle DHTML Edit est similaire à n’importe quel autre contrôle ATL, sauf le contrôle DHTML Edit inclut une interface de dispatch supplémentaire. Voir la figure dans [identification des éléments du projet de contrôle DHTML Edit](../atl/identifying-the-elements-of-the-dhtml-control-project.md) pour obtenir une illustration des interfaces fournies dans le projet DHTML par défaut.

Vous pouvez afficher le contrôle ATL DHTML dans un navigateur Web ou un autre conteneur, tels que le contrôle ActiveX Test Container.

## <a name="in-this-section"></a>Dans cette section

[Identification des éléments du projet de contrôle DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md)  
Décrit les éléments d’un projet de contrôle DHTML Edit.

[Appel de code C++ à partir de DHTML](../atl/calling-cpp-code-from-dhtml.md)  
Fournit un exemple d’appel de code C++ à partir d’un contrôle DHTML Edit.

[Création d’un contrôle ATL DHTML](../atl/creating-an-atl-dhtml-control.md)  
Répertorie les étapes de création d’un contrôle DHTML Edit.

[Test du contrôle ATL DHTML](../atl/testing-the-atl-dhtml-control.md)  
Montre comment générer et tester le projet de contrôle DHTML Edit initial.

[Modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md)  
Montre comment ajouter des fonctionnalités au contrôle.

[Test du contrôle modifié ATL DHTML](../atl/testing-the-modified-atl-dhtml-control.md)  
Montre comment générer et tester la fonctionnalité ajoutée au contrôle.

## <a name="related-sections"></a>Rubriques connexes

[ATL](../atl/active-template-library-atl-concepts.md)  
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

