---
title: Construction d’une étape et en deux étapes d’objets | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c53f99932887acad4d2eab5c15ed73b66b359fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346010"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construction d'objets en une et en deux étapes
Vous avez le choix entre deux techniques pour créer des objets graphiques, tels que des stylets et des pinceaux :  
  
-   *Construction d’une étape*: construction et initialisation de l’objet en une seule phase, toutes les données avec le constructeur.  
  
-   *Construction en deux étapes*: construction et initialisation de l’objet en deux étapes séparées. Le constructeur crée l’objet et l’initialise une fonction d’initialisation.  
  
 Construction en deux étapes est toujours plus sûre. Dans la construction d’une étape, le constructeur peut lever une exception si vous fournissez des arguments incorrects ou l’allocation de mémoire échoue. Ce problème est évité par une construction en deux étapes, bien que vous n’avez pas à la recherche de l’échec. Dans les deux cas, la destruction de l’objet est le même processus.  
  
> [!NOTE]
>  Ces techniques s’appliquent à la création des objets, de pas qu’il soit graphique.  
  
## <a name="example-of-both-construction-techniques"></a>Exemple de ces deux Techniques de Construction  
 L’exemple suivant illustre les deux méthodes de construction d’un objet pen :  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Objets graphiques](../mfc/graphic-objects.md)  
  
-   [Sélection d’un objet graphique dans un contexte de périphérique](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [Contextes de périphérique](../mfc/device-contexts.md)  
  
-   [Dessin dans une vue](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objets graphiques](../mfc/graphic-objects.md)

