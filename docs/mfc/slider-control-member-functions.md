---
description: 'En savoir plus sur : fonctions membres de contrôle Slider'
title: Fonctions membres de contrôle Slider
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
ms.openlocfilehash: 57108872a779bc4876be89afd5b81008f69a0837
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216897"
---
# <a name="slider-control-member-functions"></a>Fonctions membres de contrôle Slider

Une application peut appeler les fonctions membres du contrôle Slider pour récupérer des informations sur le contrôle Slider ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) et modifier ses caractéristiques.

Pour récupérer la position du curseur (autrement dit, la valeur choisie par l’utilisateur), utilisez la fonction membre [GetPos](../mfc/reference/csliderctrl-class.md#getpos) . Pour définir la position du curseur, utilisez la fonction membre [SetPos](../mfc/reference/csliderctrl-class.md#setpos) . À tout moment, vous pouvez utiliser la `VerifyPos` fonction membre pour vous assurer que le curseur se trouve entre les valeurs minimale et maximale.

La plage d’un contrôle Slider est l’ensemble de valeurs contiguës que le contrôle Slider peut représenter. La plupart des applications utilisent la fonction membre [SetRange](../mfc/reference/csliderctrl-class.md#setrange) pour définir la plage d’un contrôle Slider lors de sa création. Les applications peuvent modifier dynamiquement la plage après la création du contrôle Slider à l’aide des fonctions membres [SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) et [SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin) . Une application qui autorise la modification dynamique de la plage récupère généralement les paramètres de la plage finale lorsque l’utilisateur a fini de travailler avec le contrôle Slider. Pour récupérer ces paramètres, utilisez les fonctions membres [GetRange](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax)et [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) .

Une application peut utiliser le style TBS_AUTOTICKS pour afficher automatiquement les graduations d’un contrôle Slider. Toutefois, si une application doit contrôler la position ou la fréquence des graduations, il est possible d’utiliser un certain nombre de fonctions membres.

Pour définir la position d’une graduation, une application peut utiliser la fonction membre [SetTic](../mfc/reference/csliderctrl-class.md#settic) . La fonction membre [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) permet à une application de définir des graduations qui s’affichent à des intervalles réguliers dans la plage du contrôle Slider. Par exemple, l’application peut utiliser cette fonction membre pour afficher uniquement 10 graduations dans une plage comprise entre 1 et 100.

Pour récupérer l’index dans la plage correspondant à une graduation, utilisez la fonction membre [GetTic](../mfc/reference/csliderctrl-class.md#gettic) . La fonction membre [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) récupère un tableau de ces index. Pour récupérer la position d’une graduation, dans les coordonnées clientes, utilisez la fonction membre [GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) . Une application peut récupérer le nombre de graduations à l’aide de la fonction membre [GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) .

La fonction membre [ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) supprime toutes les graduations d’un contrôle Slider.

La taille de ligne d’un contrôle Slider détermine la distance de déplacement du curseur lorsqu’une application reçoit un message de notification TB_LINEDOWN ou TB_LINEUP. De même, la taille de la page détermine la réponse aux messages de notification TB_PAGEDOWN et TB_PAGEUP. Les applications peuvent récupérer et définir les valeurs de la ligne et de la taille de la page à l’aide des fonctions membres [GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize), [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize), [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize)et [setPageSize](../mfc/reference/csliderctrl-class.md#setpagesize) .

Une application peut utiliser des fonctions membres pour récupérer les dimensions d’un contrôle Slider. La fonction membre [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) récupère le rectangle englobant pour le curseur. La fonction membre [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect) récupère le rectangle englobant pour le canal du contrôle Slider. (Le canal est la zone sur laquelle le curseur se déplace et qui contient la surbrillance lorsqu’une plage est sélectionnée.)

Si un contrôle Slider a le style TBS_ENABLESELRANGE, l’utilisateur peut sélectionner une plage de valeurs contiguës à partir de celui-ci. Un certain nombre de fonctions membres permettent d’ajuster dynamiquement la plage de sélection. La fonction membre [SetSelection](../mfc/reference/csliderctrl-class.md#setselection) définit les positions de début et de fin d’une sélection. Lorsque l’utilisateur a fini de définir une plage de sélection, une application peut récupérer les paramètres à l’aide de la fonction membre [GetSelection](../mfc/reference/csliderctrl-class.md#getselection) . Pour effacer la sélection d’un utilisateur, utilisez la fonction membre [ClearSel](../mfc/reference/csliderctrl-class.md#clearsel) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
