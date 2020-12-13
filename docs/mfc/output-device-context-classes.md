---
description: 'En savoir plus sur : classes de sortie (contexte de périphérique)'
title: Classes de sortie (contexte de périphérique)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: e148999f2423165e7026bf68970fe9fc145930d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331781"
---
# <a name="output-device-context-classes"></a>Classes de sortie (contexte de périphérique)

Ces classes encapsulent les différents types de contextes de périphérique disponibles dans Windows.

La plupart des classes suivantes encapsulent un handle vers un contexte de périphérique Windows. Un contexte de périphérique est un objet Windows qui contient des informations sur les attributs de dessin d’un appareil, tel qu’un écran ou une imprimante. Tous les appels de dessin sont effectués à l’aide d’un objet de contexte d’appareil. Les classes supplémentaires dérivées de `CDC` encapsulent des fonctionnalités de contexte de périphérique spécialisées, notamment la prise en charge des fichiers Windows.

[CDC](reference/cdc-class.md)<br/>
Classe de base pour les contextes de périphérique. Utilisé directement pour accéder à l’affichage entier et pour accéder à des contextes non affichés, tels que des imprimantes.

[CPaintDC](reference/cpaintdc-class.md)<br/>
Contexte d’affichage utilisé dans les `OnPaint` fonctions membres de Windows. Appelle automatiquement la `BeginPaint` construction et la `EndPaint` destruction.

[CClientDC](reference/cclientdc-class.md)<br/>
Contexte d’affichage pour les zones clientes de Windows. Utilisé, par exemple, pour dessiner dans une réponse immédiate aux événements de souris.

[CWindowDC](reference/cwindowdc-class.md)<br/>
Contexte d’affichage pour les fenêtres entières, y compris les zones clientes et non clientes.

[CMetaFileDC](reference/cmetafiledc-class.md)<br/>
Contexte de périphérique pour les fichiers Windows. Un métafichier Windows contient une séquence de commandes GDI (Graphics Device Interface) qui peuvent être relues pour créer une image. Les appels effectués aux fonctions membres d’un `CMetaFileDC` sont enregistrés dans un métafichier.

## <a name="related-classes"></a>Classes connexes

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Contient des paires de coordonnées (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Contient la distance, les positions relatives ou les valeurs jumelées.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Contient les coordonnées des zones rectangulaires.

[CRgn](reference/crgn-class.md)<br/>
Encapsule une région GDI pour manipuler une zone elliptique, polygonale ou irrégulière dans une fenêtre. Utilisé conjointement avec les fonctions membres de découpage dans la classe `CDC` .

[CRectTracker](reference/crecttracker-class.md)<br/>
Affiche et gère l’interface utilisateur pour le redimensionnement et le déplacement d’objets rectangulaires.

[CColorDialog](reference/ccolordialog-class.md)<br/>
Fournit une boîte de dialogue standard pour la sélection d’une couleur.

[CFontDialog](reference/cfontdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour la sélection d’une police.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour l’impression d’un fichier.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
