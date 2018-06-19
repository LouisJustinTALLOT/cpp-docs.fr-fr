---
title: Procédure d’impression par défaut | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2cf5b4a9bda3506a9558d5b723020dfe6d43396
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358913"
---
# <a name="how-default-printing-is-done"></a>Impression par défaut
Cet article explique le processus d'impression par défaut dans Windows en termes de framework MFC.  
  
 Dans les applications MFC, la classe d'affichage fournit une fonction membre nommée `OnDraw` qui contient le code de dessin. `OnDraw` prend un pointeur vers un [CDC](../mfc/reference/cdc-class.md) objet en tant que paramètre. Cet objet `CDC` représente le contexte de périphérique pour recevoir l'image générée par `OnDraw`. Lorsque la fenêtre affichant le document reçoit un [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) d’un message, le framework appelle `OnDraw` et lui passe un contexte de périphérique de l’écran (un [CPaintDC](../mfc/reference/cpaintdc-class.md) objet, pour être précis). Par conséquent, la sortie de `OnDraw`passe à l'écran.  
  
 En programmation pour Windows, envoyer la sortie vers l'imprimante est très similaire à envoyer la sortie à l'écran. Cela est dû au fait que l'interface Windows GDI (Windows Graphics Device Interface) est indépendante du matériel. Vous pouvez utiliser les mêmes fonctions GDI pour afficher l'écran ou pour l'impression simplement à l'aide du contexte de périphérique. Si l'objet `CDC` que `OnDraw` reçoit représente l'imprimante, la sortie de `OnDraw`est envoyée à l'imprimante.  
  
 Ceci explique comment les applications MFC peuvent effectuer une impression simple sans effort supplémentaire de votre part. Le framework prend soin d'afficher la boîte de dialogue Imprimer et de créer un contexte de périphérique pour l'imprimante. Lorsque l'utilisateur sélectionne la commande Imprimer dans le menu Fichier, la vue passe ce contexte de périphérique à `OnDraw`, qui dessine le document sur l'imprimante.  
  
 Toutefois, il existe des différences significatives entre l'impression et l'écran. Lors de la copie, vous devez diviser le document en pages distinctes et les afficher une par une, plutôt que d'afficher n'importe quelle partie visible dans une fenêtre. En corollaire, vous devez être informé du format du papier (qu'il s'agisse de la taille des caractères, du format legal ou d'une enveloppe). Vous pouvez imprimer sous différentes orientations, telles que le mode Paysage et le mode Portrait. La bibliothèque MFC ne peut pas prévoir comment votre application traite ces questions, donc elle fournit un protocole pour pouvoir ajouter ces fonctions.  
  
 Ce protocole est décrit dans l’article [Documents multipages](../mfc/multipage-documents.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Impression](../mfc/printing.md)

