---
title: ASP, Assistant composant ASP ATL | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.asp.asp
dev_langs: C++
helpviewer_keywords: ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69d3837cc0996c0e0e0784214cfbfa6744afbf94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Assistant Composant ASP ATL
Utilisez cette page de l’Assistant composant Active Server Page ATL pour spécifier des paramètres facultatifs pour la gestion des informations et l’état associé à votre composant ASP.  
  
 **Méthodes facultatives**  
 Ajoute les méthodes ASP facultatives, **OnStartPage** et **OnEndPage**, à votre objet. Cette option doit être sélectionnée pour définir des objets intrinsèques d’Active Server Pages. Par défaut, il est sélectionné.  
  
-   **OnStartPage/OnEndPage** [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx) est appelée la première fois que le script essaie d’accéder à l’objet. **OnEndPage** est appelée lorsque l’objet a terminé le traitement du script.  
  
 **Objet intrinsèque**  
 Vous devez sélectionner le **OnStartPage/OnEndPage** option permettant de définir des objets intrinsèques ASP.  
  
|Option|Description|  
|------------|-----------------|  
|**Demande**|Fournit l’accès à l’intrinsèque Active Server Pages **demande** objet. L’objet de demande est utilisé pour passer d’une requête HTTP.|  
|**Réponse**|Fournit l’accès à l’intrinsèque Active Server Pages **réponse** objet. En réponse à une demande, l’objet Response envoie des informations au navigateur pour afficher à l’utilisateur.|  
|**Session**|Fournit l’accès à l’intrinsèque Active Server Pages **Session** objet. Le **Session** objet conserve les informations sur la session utilisateur en cours, y compris le stockage et la récupération des informations d’état.|  
|**Application**|Fournit l’accès à l’intrinsèque Active Server Pages **Application** objet. Le **Application** objet gère l’état partagé entre plusieurs objets ASP.|  
|**Serveur**|Fournit l’accès à l’intrinsèque Active Server Pages **Server** objet. Le **Server** objet vous permet de créer d’autres objets ASP.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant composant ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Composant ASP ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

