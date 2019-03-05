---
title: 'Contrôles ActiveX MFC : Optimisation'
ms.date: 09/12/2018
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
ms.openlocfilehash: 08cbb5ab0ff9b8c165e549bc2b250daebc1ce177
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288614"
---
# <a name="mfc-activex-controls-optimization"></a>Contrôles ActiveX MFC : Optimisation

Cet article explique les techniques que vous pouvez utiliser pour optimiser vos contrôles ActiveX pour de meilleures performances.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Les rubriques [activation de désactiver l’Option actif quand Visible](../mfc/turning-off-the-activate-when-visible-option.md) et [fournissant Interaction souris pendant l’inactivité](../mfc/providing-mouse-interaction-while-inactive.md) traitent des contrôles qui ne créent une fenêtre jusqu'à l’activation. La rubrique [fournissant l’Activation sans fenêtre](../mfc/providing-windowless-activation.md) décrit les contrôles jamais créent une fenêtre, même lorsqu’ils sont activés.

Windows ont deux inconvénients principaux pour les objets OLE : elles empêchent les objets d’être transparents ou non rectangulaires quand elle est active, et ils ajoutent une surcharge de grande taille à l’instanciation et l’affichage des contrôles. En règle générale, la création d’une fenêtre prend 60 pour cent du temps de création d’un contrôle. Avec une fenêtre unique partagée (généralement du conteneur) et du code dispatch, un contrôle reçoit les mêmes services de fenêtre, généralement sans perte de performances. Présence d’une fenêtre est essentiellement une surcharge inutile pour l’objet.

Certaines optimisations n’améliorent pas nécessairement les performances lorsque votre contrôle est utilisé dans certains conteneurs. Par exemple, conteneurs publiées avant 1996 ne prenait pas en charge l’activation sans fenêtre, afin d’implémenter cette fonctionnalité ne fournira pas un avantage dans les conteneurs plus anciens. Cependant, presque chaque conteneur prend en charge la persistance, afin d’optimiser le code de persistance de votre contrôle sera probablement améliorer ses performances dans n’importe quel conteneur. Si votre contrôle est spécifiquement destiné à être utilisée avec un type particulier de conteneur, vous souhaiterez effectuer des recherches parmi ces optimisations est pris en charge par ce conteneur. En général, toutefois, vous devez tenter implémentent comme nombre de ces techniques sont applicables à votre contrôle afin de garantir que votre contrôle fonctionne aussi bien qu’éventuellement dans un large éventail de conteneurs.

Vous pouvez implémenter la plupart de ces optimisations par le biais du [Assistant contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md), dans le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page.

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Options de l’optimisation MFC OLE de l’Assistant contrôle ActiveX

|Paramètre de contrôle dans l’Assistant contrôle ActiveX MFC|Action|Complément d'information|
|-------------------------------------------------------|------------|----------------------|
|**Activer lorsqu’elle est visible** case à cocher|Effacer|[Désactivation de l’activer lorsque Option est Visible](../mfc/turning-off-the-activate-when-visible-option.md)|
|**L’activation sans fenêtre** case à cocher|Sélectionner|[Mise à disposition de l’activation sans fenêtre](../mfc/providing-windowless-activation.md)|
|**Contexte de périphérique non découpé** case à cocher|Sélectionner|[Utilisation d’un contexte d’appareil non découpé](../mfc/using-an-unclipped-device-context.md)|
|**Activation sans scintillement** case à cocher|Sélectionner|[Mise à disposition de l’activation sans scintillement](../mfc/providing-flicker-free-activation.md)|
|**Notifications du pointeur de cas d’inactivité de la souris** case à cocher|Sélectionner|[Prise en charge de l’interaction souris pendant l’inactivité](../mfc/providing-mouse-interaction-while-inactive.md)|
|**Code de dessin optimisé** case à cocher|Sélectionner|[Optimisation du contrôle de dessin](../mfc/optimizing-control-drawing.md)|

Pour obtenir des informations détaillées sur les fonctions membres qui implémentent ces optimisations, consultez [COleControl](../mfc/reference/colecontrol-class.md).

Pour plus d'informations, voir :

- [Optimisation de la persistance et de l’initialisation](../mfc/optimizing-persistence-and-initialization.md)

- [Mise à disposition de l’activation sans fenêtre](../mfc/providing-windowless-activation.md)

- [Désactivation de l’activer lorsque Option est Visible](../mfc/turning-off-the-activate-when-visible-option.md)

- [Prise en charge de l’interaction souris pendant l’inactivité](../mfc/providing-mouse-interaction-while-inactive.md)

- [Mise à disposition de l’activation sans scintillement](../mfc/providing-flicker-free-activation.md)

- [Utilisation d’un contexte d’appareil non découpé](../mfc/using-an-unclipped-device-context.md)

- [Optimisation du contrôle de dessin](../mfc/optimizing-control-drawing.md)

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
