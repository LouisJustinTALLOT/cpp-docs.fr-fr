---
title: Fonctions membres de contrôle Slider | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3793ca47aa0537d5ca8d6858c165fc2c5ac64943
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383443"
---
# <a name="slider-control-member-functions"></a>Fonctions membres de contrôle Slider
Une application peut appeler le curseur de fonctions de membre d’un contrôle à récupérer des informations sur le contrôle slider ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) et pour modifier ses caractéristiques.  
  
 Pour récupérer la position du curseur (autrement dit, la valeur l’utilisateur a choisi), utilisez la [GetPos](../mfc/reference/csliderctrl-class.md#getpos) fonction membre. Pour définir la position du curseur, utilisez la [fonction membre SetPos](../mfc/reference/csliderctrl-class.md#setpos) fonction membre. À tout moment, vous pouvez utiliser la `VerifyPos` fonction membre pour vous assurer que le curseur se trouve entre les valeurs minimales et maximale.  
  
 La plage d’un contrôle slider est l’ensemble de valeurs contiguës que le contrôle de curseur peut représenter. La plupart des applications utilisent le [SetRange](../mfc/reference/csliderctrl-class.md#setrange) fonction membre pour définir la plage d’un contrôle slider lors de sa création. Les applications peuvent modifier dynamiquement la plage après le contrôle de curseur a été créé à l’aide de la [fonctions membres SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) et [SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin) fonctions membres. Une application qui permet la plage à modifier dynamiquement généralement récupère les paramètres de plage finaux lorsque l’utilisateur a fini de travailler avec le contrôle slider. Pour récupérer ces paramètres, utilisez le [GetRange](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax), et [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) fonctions membres.  
  
 Une application peut utiliser les `TBS_AUTOTICKS` style d’avoir des graduations d’un contrôle slider s’affichent automatiquement. Si une application a besoin de contrôler la position ou la fréquence des graduations, toutefois, un nombre de fonctions membres peut être utilisé.  
  
 Pour définir la position d’une graduation, une application peut utiliser le [SetTic](../mfc/reference/csliderctrl-class.md#settic) fonction membre. Le [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) fonction membre permet à une application de définir des graduations qui apparaissent à intervalles réguliers dans la plage du contrôle de curseur. Par exemple, l’application peut utiliser cette fonction membre pour afficher uniquement 10 graduations dans une plage comprise entre 1 et 100.  
  
 Pour récupérer l’index de la plage correspondant à une graduation, utilisez le [fonction membre GetTic](../mfc/reference/csliderctrl-class.md#gettic) fonction membre. Le [fonction membre GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) fonction membre récupère un tableau de ces index. Pour récupérer la position d’une graduation, en coordonnées clientes, utilisez la [fonction membre GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) fonction membre. Une application peut extraire le nombre de graduations à l’aide de la [fonction membre GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) fonction membre.  
  
 Le [fonction membre ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) fonction membre supprime toutes les marques de graduation d’un contrôle slider.  
  
 Taille de la ligne d’un contrôle slider détermine la distance, le curseur se déplace lorsqu’une application reçoit un **quel** ou **TB_LINEUP** message de notification. De même, la taille de page détermine la réponse à la **TB_PAGEDOWN** et **TB_PAGEUP** messages de notification. Les applications peuvent récupérer et définir les valeurs de taille de ligne et de page à l’aide de la [fonctions membres GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize), [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize), [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize), et [SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize) fonctions membres.  
  
 Une application peut utiliser des fonctions membres pour extraire les dimensions d’un contrôle slider. Le [fonction membre GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) fonction membre récupère le rectangle englobant pour le curseur. Le [fonction membre GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect) fonction membre récupère le rectangle englobant pour le canal du contrôle de curseur. (Le canal est la zone sur laquelle le curseur se déplace et qui contient la mise en surbrillance lorsqu’une plage est sélectionnée).  
  
 Si un contrôle slider a le `TBS_ENABLESELRANGE` style, l’utilisateur peut sélectionner une plage de valeurs contiguës à partir de celui-ci. Un nombre de fonctions membres autorise la sélection d’être ajustée de façon dynamique. Le [SetSelection](../mfc/reference/csliderctrl-class.md#setselection) fonction membre définit le début et fin des positions d’une sélection. Lorsque l’utilisateur a terminé de définir une plage de sélection, une application peut récupérer les paramètres à l’aide de la [GetSelection](../mfc/reference/csliderctrl-class.md#getselection) fonction membre. Pour effacer la sélection d’un utilisateur, utilisez la [fonction membre ClearSel](../mfc/reference/csliderctrl-class.md#clearsel) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

