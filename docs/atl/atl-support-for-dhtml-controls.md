---
description: 'En savoir plus sur : prise en charge ATL pour les contrôles DHTML'
title: Prise en charge ATL pour les contrôles DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: 7527527bc5574470fd361bae2375c25ce9345f3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148588"
---
# <a name="atl-support-for-dhtml-controls"></a>Prise en charge ATL pour les contrôles DHTML

À l’aide d’ATL, vous pouvez créer un contrôle avec la fonctionnalité DHTML (Dynamic HTML). Un contrôle ATL DHTML :

- Héberge le contrôle WebBrowser.

- Spécifie, à l’aide de HTML, l’interface utilisateur (IU) du contrôle DHTML.

- Accède à l’objet WebBrowser et à ses méthodes par le biais de son interface [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)).

- Gère la communication entre le code C++ et HTML.

Un contrôle DHTML est semblable à tout autre contrôle ATL, sauf que le contrôle DHTML comprend une interface de dispatch supplémentaire. Pour obtenir une illustration des interfaces fournies dans le projet DHTML par défaut, voir la figure relative à l' [identification des éléments du projet de contrôle DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) .

Vous pouvez afficher le contrôle ATL DHTML dans un navigateur Web ou un autre conteneur, tel que ActiveX Control Test Container.

## <a name="in-this-section"></a>Dans cette section

[Identification des éléments du projet de contrôle DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
Décrit les éléments d’un projet de contrôle DHTML.

[Appeler du code C++ à partir de DHTML](../atl/calling-cpp-code-from-dhtml.md)<br/>
Fournit un exemple d’appel de code C++ à partir d’un contrôle DHTML.

[Création d’un contrôle ATL DHTML](../atl/creating-an-atl-dhtml-control.md)<br/>
Répertorie les étapes de création d’un contrôle DHTML.

[Test du contrôle ATL DHTML](../atl/testing-the-atl-dhtml-control.md)<br/>
Montre comment générer et tester le projet de contrôle DHTML initial.

[Modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md)<br/>
Montre comment ajouter des fonctionnalités au contrôle.

[Test du contrôle ATL DHTML modifié](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
Montre comment générer et tester les fonctionnalités ajoutées du contrôle.

## <a name="related-sections"></a>Sections connexes

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).
