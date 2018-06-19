---
title: 'Contrôles ActiveX MFC : Optimisation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], windowless
- flicker-free ActiveX controls
- MFC ActiveX controls [MFC], mouse interaction
- device contexts, unclipped for MFC ActiveX controls
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- MFC ActiveX controls [MFC], flicker-free
- windowless MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- optimizing performance, ActiveX controls
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c91f147637b53250f8d373af9950d6205c82d3e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355309"
---
# <a name="mfc-activex-controls-optimization"></a>Contrôles ActiveX MFC : optimisation
Cet article explique les techniques que vous pouvez utiliser pour optimiser vos contrôles ActiveX pour de meilleures performances.  
  
 Les rubriques [activation de désactiver l’Option actif quand il Visible](../mfc/turning-off-the-activate-when-visible-option.md) et [fournissant Interaction souris pendant l’inactivité](../mfc/providing-mouse-interaction-while-inactive.md) traitent des contrôles qui ne créent une fenêtre jusqu'à ce qu’activée. La rubrique [fournissant l’Activation sans fenêtre](../mfc/providing-windowless-activation.md) décrit les contrôles jamais créent une fenêtre, même lorsqu’ils sont activés.  
  
 Windows ont deux inconvénients principaux pour les objets OLE : elles empêchent les objets transparents ou non rectangulaires lorsqu’il est actif, et ils ajoutent une charge de grande taille à l’instanciation et l’affichage de contrôles. En règle générale, la création d’une fenêtre prend 60 pour cent de l’heure de création d’un contrôle. Avec une fenêtre unique partagée (généralement du conteneur) et du code dispatch, un contrôle reçoit les mêmes services de fenêtre, généralement sans perte de performances. Une fenêtre est principalement un traitement inutile pour l’objet.  
  
 Certaines optimisations n’améliorent pas nécessairement les performances lorsque votre contrôle est utilisé dans certains conteneurs. Par exemple, les conteneurs publiées avant 1996 ne prenait pas en charge l’activation sans fenêtre, afin d’implémenter cette fonctionnalité ne fournira pas des avantages dans les conteneurs plus anciens. Toutefois, presque chaque conteneur prend en charge la persistance, afin d’optimiser le code de persistance de votre contrôle probablement améliore ses performances dans n’importe quel conteneur. Si votre contrôle est conçu spécifiquement pour être utilisé avec un type particulier de conteneur, vous souhaiterez effectuer des recherches sur laquelle de ces optimisations est pris en charge par ce conteneur. En général, toutefois, vous devriez implémentent comme nombre de ces techniques sont applicables à votre contrôle afin de garantir que votre contrôle exécute éventuellement optimal dans un grand nombre de conteneurs.  
  
 Vous pouvez implémenter la plupart de ces optimisations via la [Assistant contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md), dans le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page.  
  
### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Options de l’optimisation MFC OLE de l’Assistant contrôle ActiveX  
  
|Paramètre de contrôle dans l’Assistant contrôle ActiveX MFC|Action|Complément d'information|  
|-------------------------------------------------------|------------|----------------------|  
|**Activer lorsqu’elle est visible** case à cocher|Effacer|[Désactivation de l’activer quand Option Visible](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**L’activation sans fenêtre** case à cocher|Sélectionner|[Mise à disposition de l’activation sans fenêtre](../mfc/providing-windowless-activation.md)|  
|**Contexte de périphérique non découpé** case à cocher|Sélectionner|[Utilisation d’un contexte d’appareil non découpé](../mfc/using-an-unclipped-device-context.md)|  
|**Activation sans scintillement** case à cocher|Sélectionner|[Mise à disposition de l’activation sans scintillement](../mfc/providing-flicker-free-activation.md)|  
|**Notifications du pointeur pendant l’inactivité de la souris** case à cocher|Sélectionner|[Prise en charge de l’interaction souris pendant l’inactivité](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**Code de dessin optimisé** case à cocher|Sélectionner|[Optimisation du contrôle de dessin](../mfc/optimizing-control-drawing.md)|  
  
 Pour obtenir des informations détaillées sur les fonctions membres qui implémentent ces optimisations, consultez [COleControl](../mfc/reference/colecontrol-class.md). Les fonctions membres sont répertoriées à l’aide, tel que [opérations sans fenêtre](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) et [fonctions de gestion de pointeur inactif](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df).  
  
 Pour plus d'informations, voir :  
  
-   [Optimisation de la persistance et de l’initialisation](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [Mise à disposition de l’activation sans fenêtre](../mfc/providing-windowless-activation.md)  
  
-   [Désactivation de l’activer quand Option Visible](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [Prise en charge de l’interaction souris pendant l’inactivité](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [Mise à disposition de l’activation sans scintillement](../mfc/providing-flicker-free-activation.md)  
  
-   [Utilisation d’un contexte d’appareil non découpé](../mfc/using-an-unclipped-device-context.md)  
  
-   [Optimisation du contrôle de dessin](../mfc/optimizing-control-drawing.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

