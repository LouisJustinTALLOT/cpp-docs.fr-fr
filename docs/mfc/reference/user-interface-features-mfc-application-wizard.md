---
title: Fonctionnalités d’Interface utilisateur, Assistant Application MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.ui
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29961e7b597683d3735203de9a47646b2a320469
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722551"
---
# <a name="user-interface-features-mfc-application-wizard"></a>Fonctionnalités de l'interface utilisateur, Assistant Application MFC

Cette rubrique explique les options que vous pouvez utiliser pour spécifier l’apparence de votre application. Les fonctionnalités d’interface utilisateur disponibles pour votre projet varient selon le type d’application spécifié dans le [Type d’Application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md) page de l’Assistant Application MFC. Par exemple, si vous créez une application d’interface monodocument, vous ne pouvez pas ajouter styles du frame enfant.  
  
- **Styles du frame principal**

   Définit les fonctionnalités du frame de fenêtre principale de votre application.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Frame épais**|Crée une fenêtre possédant une bordure de dimensionnement. Valeur par défaut.|  
   |**Bouton réduire**|Inclut un réduire dans la fenêtre frame principale. Valeur par défaut.|  
   |**Bouton d’agrandissement**|Inclut un agrandissement dans la fenêtre frame principale. Valeur par défaut.|  
   |**Réduite**|Ouvre la fenêtre frame principale en tant qu’icône.|  
   |**Agrandie**|Ouvre la fenêtre frame principale à la taille totale de l’affichage.|  
   |**Menu système**|Inclut un menu système dans la fenêtre frame principale. Valeur par défaut.|  
   |**À propos de la zone**|Inclut un **sur** pour l’application. L’utilisateur peut accéder à cette boîte à partir de l’application **aide** menu. La valeur par défaut et non modifiable, sauf si vous sélectionnez **basée sur un dialogue**, dans le [Type d’Application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md) page.<br /><br /> **Remarque** en règle générale, une option non disponible indique que l’Assistant ne s’applique pas l’option au projet, si la case à cocher de l’élément non disponible est activée ou désactivée. Dans ce cas, l’Assistant ajoute toujours un **sur** boîte au projet, sauf si vous spécifiez d’abord le projet en tant que boîte de dialogue en fonction et décochez la case.|  
   |**Barre d’état initiale**|Ajoute une barre d’état à votre application. La barre d’état contient des indicateurs automatiques pour les clés de Verr. MAJ, VERR. NUM et défil du clavier et une ligne de message qui affiche l’aide des chaînes pour les commandes de menu et barre d’outils de boutons. Cliquer sur cette option ajoute également des commandes de menu pour afficher ou masquer la barre d’état. Par défaut, une application a une barre d’état. Non disponible pour les types d’application basée sur la boîte de dialogue.|  
   |**Fenêtre fractionnée**|Fournit une barre de fractionnement. La barre de fractionnement fractionne les vues principales de l’application. Dans une application d’interface (multidocument MDI) document, fenêtre du client du frame enfant MDI est une fenêtre fractionnée, et dans une application SDI (interface) de document unique et plusieurs applications de document de niveau supérieur, fenêtre cliente du frame principal est une fenêtre fractionnée. Non disponible pour les types d’application basée sur la boîte de dialogue.|  
  
- **Styles du frame enfant**

   Spécifie l’apparence et l’état initial des frames enfants dans votre application. Styles du frame enfant sont disponibles pour les applications MDI uniquement.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Bouton réduire enfant**|Spécifie si une fenêtre enfant possède un bouton réduire (activé par défaut).|  
   |**Bouton Agrandir enfant**|Spécifie si une fenêtre enfant possède un bouton Agrandir (activé par défaut).|  
   |**Enfant agrandi**|Spécifie si une fenêtre enfant est initialement agrandie en définissant le cs.style indicateur WS_MAXIMIZE dans le [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow) fonction membre de `CChildFrame`.|  
  
- **Barres de commandes (menu, barre d’outils/ruban)**

   Indique si votre application inclut des menus, barres d’outils et/ou un ruban. Non disponible pour les applications basées sur la boîte de dialogue.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Utiliser un menu classique**|Spécifie que votre application contient un menu classique, non déplaçables.|  
   |**Utiliser une barre d’outils d’ancrage classique**|Ajoute une barre d’outils Windows standard à votre application. La barre d’outils contient des boutons pour la création d’un document ; ouvrir et enregistrer des fichiers de document ; Couper, copier, coller ou l’impression de texte ; et en entrant le mode d’aide. L’activation de cette option ajoute également des commandes de menu pour afficher ou masquer la barre d’outils.|  
   |**Utiliser une barre d’outils de style navigateur**|Ajoute une barre d’outils Internet Explorer-style à votre application.|  
   |**Utiliser une barre de menus et la barre d’outils**|Indique que votre application contienne une barre de menus déplaçable et une barre d’outils.|  
   |**Images et des barres d’outils de défini par l’utilisateur**|Permet à l’utilisateur de personnaliser la barre d’outils et les images de barre d’outils lors de l’exécution.|  
   |**Comportement de menu personnalisé**|Spécifie si le menu contient la liste complète des éléments de l’ouverture, ou si elle contient uniquement les commandes que l’utilisateur utilise fréquemment.|  
   |**Utiliser un ruban**|Utilise un ruban de type Office 2007 dans votre application au lieu d’une barre de menus ou la barre d’outils.|  
  
- **Titre de la boîte de dialogue**

   Pour [classe CDialog](../../mfc/reference/cdialog-class.md)-uniquement, les applications basées sur ce titre s’affiche dans la barre de titre de la boîte de dialogue. Pour modifier ce champ, vous devez d’abord sélectionner le **basée sur un dialogue** sous **type d’Application**. Pour plus d’informations, consultez [Type d’Application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)

