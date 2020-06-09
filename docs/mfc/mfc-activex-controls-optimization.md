---
title: 'Contrôles ActiveX MFC : optimisation'
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
ms.openlocfilehash: b4e12889ca1bb5f4bb423a1f1ede1c396f8d60b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615398"
---
# <a name="mfc-activex-controls-optimization"></a>Contrôles ActiveX MFC : optimisation

Cet article explique les techniques que vous pouvez utiliser pour optimiser vos contrôles ActiveX afin d’améliorer les performances.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Les rubriques [désactivant l’option Activer quand](turning-off-the-activate-when-visible-option.md) elle est visible et l' [interaction avec la souris pendant qu’elle est inactive](providing-mouse-interaction-while-inactive.md) discutent des contrôles qui ne créent pas de fenêtre jusqu’à ce qu’ils soient activés. La rubrique [fournissant une activation sans fenêtre](providing-windowless-activation.md) traite des contrôles qui ne créent jamais de fenêtre, même lorsqu’ils sont activés.

Windows présente deux inconvénients majeurs pour les objets OLE : ils empêchent les objets d’être transparents ou non rectangulaires lorsqu’ils sont actifs, et ils ajoutent une surcharge importante à l’instanciation et à l’affichage des contrôles. En règle générale, la création d’une fenêtre prend 60% de la durée de création d’un contrôle. Avec une seule fenêtre partagée (généralement le du conteneur) et un code de distribution, un contrôle reçoit les mêmes services de fenêtre, généralement sans perte de performances. Le fait de disposer d’une fenêtre est surtout une surcharge inutile pour l’objet.

Certaines optimisations n’améliorent pas nécessairement les performances lorsque votre contrôle est utilisé dans certains conteneurs. Par exemple, les conteneurs antérieurs à 1996 ne prenaient pas en charge l’activation sans fenêtre. par conséquent, l’implémentation de cette fonctionnalité ne constitue pas un avantage dans les conteneurs plus anciens. Toutefois, presque tous les conteneurs prennent en charge la persistance. par conséquent, l’optimisation du code de persistance de votre contrôle améliorera probablement ses performances dans n’importe quel conteneur. Si votre contrôle est spécifiquement destiné à être utilisé avec un type particulier de conteneur, vous souhaiterez peut-être Rechercher les optimisations prises en charge par ce conteneur. En général, toutefois, vous devez essayer d’implémenter autant de ces techniques que celles applicables à votre contrôle particulier pour vous assurer que votre contrôle fonctionne aussi bien que possible dans un grand tableau de conteneurs.

Vous pouvez implémenter un grand nombre de ces optimisations par le biais de l' [Assistant contrôle ActiveX MFC](reference/mfc-activex-control-wizard.md), sur la page [paramètres du contrôle](reference/control-settings-mfc-activex-control-wizard.md) .

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Options d’optimisation OLE de l’Assistant contrôle ActiveX MFC

|Paramètre de contrôle dans l’Assistant contrôle ActiveX MFC|Action|Informations complémentaires|
|-------------------------------------------------------|------------|----------------------|
|Case à cocher **activer quand** elle est visible|Désactiver|[Désactivation de l’option Activer quand elle est visible](turning-off-the-activate-when-visible-option.md)|
|Case à cocher **activation sans fenêtre**|Sélectionnez|[Mise à disposition de l'activation sans fenêtre](providing-windowless-activation.md)|
|Case à cocher du **contexte de périphérique non découpé**|Sélectionnez|[Utilisation d’un contexte d’appareil non découpé](using-an-unclipped-device-context.md)|
|Case à cocher **activation sans scintillement**|Sélectionnez|[Mise à disposition de l’activation sans scintillement](providing-flicker-free-activation.md)|
|Case à cocher **des notifications de pointeur de souris en cas d’inactivité**|Sélectionnez|[Prise en charge de l’interaction souris pendant l’inactivité](providing-mouse-interaction-while-inactive.md)|
|Case à cocher **Code de dessin optimisé**|Sélectionnez|[Optimisation du dessin de contrôle](optimizing-control-drawing.md)|

Pour plus d’informations sur les fonctions membres qui implémentent ces optimisations, consultez [COleControl](reference/colecontrol-class.md).

Pour plus d'informations, voir :

- [Optimisation de la persistance et de l’initialisation](optimizing-persistence-and-initialization.md)

- [Mise à disposition de l'activation sans fenêtre](providing-windowless-activation.md)

- [Désactivation de l’option Activer quand elle est visible](turning-off-the-activate-when-visible-option.md)

- [Prise en charge de l’interaction souris pendant l’inactivité](providing-mouse-interaction-while-inactive.md)

- [Mise à disposition de l’activation sans scintillement](providing-flicker-free-activation.md)

- [Utilisation d’un contexte d’appareil non découpé](using-an-unclipped-device-context.md)

- [Optimisation du dessin de contrôle](optimizing-control-drawing.md)

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
