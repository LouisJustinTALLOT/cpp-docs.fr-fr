---
description: 'En savoir plus sur : ASP, ATL Active Server Assistant composant de page'
title: ASP, Assistant Composant ASP ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.asp
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
ms.openlocfilehash: e9cc11cf60c3a87d6891c98a72eb240729d1a739
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165535"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Assistant Composant ASP ATL

Utilisez cette page de l’Assistant composant de page Active Server ATL pour spécifier des paramètres facultatifs pour la gestion des informations et de l’État lié à votre composant ASP.

- **Méthodes facultatives**

   Ajoute les méthodes ASP facultatives, **OnStartPage** et **OnEndPage**, à votre objet. Vous devez sélectionner cette option pour définir des objets intrinsèques de pages de Active Server. Par défaut, il est sélectionné.

- **OnStartPage/OnEndPage**

   [OnStartPage](/previous-versions//ms691624\(v=vs.85\)) est appelé la première fois que le script tente d’accéder à l’objet. **OnEndPage** est appelé lorsque l’objet a terminé le traitement du script.

- **Objet intrinsèque**

   Vous devez sélectionner l’option **OnStartPage/OnEndPage** pour définir des objets intrinsèques ASP.

|Option|Description|
|------------|-----------------|
|**Requête**|Fournit l’accès à l’objet de **requête** intrinsèque pages Active Server. L’objet de requête est utilisé pour passer une requête HTTP.|
|**Réponse**|Fournit l’accès à l’objet de **réponse** intrinsèque pages Active Server. En réponse à une demande, l’objet réponse envoie des informations au navigateur pour les afficher à l’utilisateur.|
|**Session**|Fournit l’accès à l’objet de **session** intrinsèque pages Active Server. L’objet **session** conserve les informations relatives à la session utilisateur en cours, y compris le stockage et la récupération des informations d’État.|
|**Application**|Fournit l’accès à l’objet d' **application** intrinsèque pages Active Server. L’objet **application** gère l’état partagé entre plusieurs objets ASP.|
|**Serveur**|Fournit l’accès à l’objet **serveur** intrinsèque pages Active Server. L’objet **serveur** vous permet de créer d’autres objets ASP.|

## <a name="see-also"></a>Voir aussi

[Assistant Composant ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Composant ASP ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
