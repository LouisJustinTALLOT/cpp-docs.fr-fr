---
title: ASP, Assistant Composant ASP ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.asp
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
ms.openlocfilehash: efc82edf00a9bb2f2facbd883ef88f1d093e0133
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290194"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Assistant Composant ASP ATL

Utilisez cette page de l’Assistant composant Active Server Page ATL pour spécifier des paramètres facultatifs pour la gestion des informations et l’état associé à votre composant ASP.

- **Méthodes facultatives**

   Ajoute les méthodes ASP facultatives, **OnStartPage** et **OnEndPage**, à votre objet. Cette option doit être sélectionnée pour définir des objets intrinsèques Active Server Pages. Par défaut, il est sélectionné.

- **OnStartPage/OnEndPage**

   [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx) est appelée la première fois que le script tente d’accéder à l’objet. **OnEndPage** est appelée lorsque l’objet a terminé le script de traitement.

- **Objet intrinsèque**

   Vous devez sélectionner le **OnStartPage/OnEndPage** option permettant de définir des objets intrinsèques ASP.

|Option|Description|
|------------|-----------------|
|**Requête**|Fournit l’accès à l’intrinsèque Active Server Pages **demande** objet. L’objet de requête est utilisé pour transmettre une requête HTTP.|
|**Réponse**|Fournit l’accès à l’intrinsèque Active Server Pages **réponse** objet. En réponse à une demande, l’objet de réponse envoie des informations au navigateur pour afficher à l’utilisateur.|
|**Session**|Fournit l’accès à l’intrinsèque Active Server Pages **Session** objet. Le **Session** objet conserve les informations sur la session utilisateur en cours, y compris les stocker et récupérer des informations d’état.|
|**Application**|Fournit l’accès à l’intrinsèque Active Server Pages **Application** objet. Le **Application** objet gère l’état est partagé entre plusieurs objets ASP.|
|**Serveur**|Fournit l’accès à l’intrinsèque Active Server Pages **Server** objet. Le **Server** objet vous permet de créer d’autres objets ASP.|

## <a name="see-also"></a>Voir aussi

[Assistant Composant ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Composant ASP ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
