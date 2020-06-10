---
title: Impression par défaut
ms.date: 11/04/2016
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
ms.openlocfilehash: 9ca79ec69037b960e7c455f6ab8abd8833b9a8a0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618588"
---
# <a name="how-default-printing-is-done"></a>Impression par défaut

Cet article explique le processus d'impression par défaut dans Windows en termes de framework MFC.

Dans les applications MFC, la classe d'affichage fournit une fonction membre nommée `OnDraw` qui contient le code de dessin. `OnDraw`prend un pointeur vers un objet [CDC](reference/cdc-class.md) en tant que paramètre. Cet objet `CDC` représente le contexte de périphérique pour recevoir l'image générée par `OnDraw`. Lorsque la fenêtre affichant le document reçoit un message de [WM_PAINT](/windows/win32/gdi/wm-paint) , le Framework appelle `OnDraw` et lui passe un contexte de périphérique pour l’écran (un objet [CPaintDC](reference/cpaintdc-class.md) , pour être spécifique). Par conséquent, la sortie de `OnDraw`passe à l'écran.

En programmation pour Windows, envoyer la sortie vers l'imprimante est très similaire à envoyer la sortie à l'écran. Cela est dû au fait que l'interface Windows GDI (Windows Graphics Device Interface) est indépendante du matériel. Vous pouvez utiliser les mêmes fonctions GDI pour afficher l'écran ou pour l'impression simplement à l'aide du contexte de périphérique. Si l'objet `CDC` que `OnDraw` reçoit représente l'imprimante, la sortie de `OnDraw`est envoyée à l'imprimante.

Ceci explique comment les applications MFC peuvent effectuer une impression simple sans effort supplémentaire de votre part. Le framework prend soin d'afficher la boîte de dialogue Imprimer et de créer un contexte de périphérique pour l'imprimante. Lorsque l'utilisateur sélectionne la commande Imprimer dans le menu Fichier, la vue passe ce contexte de périphérique à `OnDraw`, qui dessine le document sur l'imprimante.

Toutefois, il existe des différences significatives entre l'impression et l'écran. Lors de la copie, vous devez diviser le document en pages distinctes et les afficher une par une, plutôt que d'afficher n'importe quelle partie visible dans une fenêtre. En corollaire, vous devez être informé du format du papier (qu'il s'agisse de la taille des caractères, du format legal ou d'une enveloppe). Vous pouvez imprimer sous différentes orientations, telles que le mode Paysage et le mode Portrait. La bibliothèque MFC ne peut pas prévoir comment votre application traite ces questions, donc elle fournit un protocole pour pouvoir ajouter ces fonctions.

Ce protocole est décrit dans l’article [documents multipages](multipage-documents.md).

## <a name="see-also"></a>Voir aussi

[Impression](printing.md)
