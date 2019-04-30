---
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
ms.openlocfilehash: 1d76570e7bfd4ce587b3803235394ec5406d30b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410198"
---
# <a name="output-device-context-classes"></a>Classes de sortie (contexte de périphérique)

Ces classes encapsulent les différents types de contextes de périphérique disponibles dans Windows.

La plupart des classes suivantes encapsulent un handle vers un contexte de périphérique Windows. Un contexte de périphérique est un objet de Windows qui contient des informations sur les attributs de dessin d’un appareil tel qu’un écran ou une imprimante. Tous les appels de dessins sont effectués via un objet de contexte de périphérique. Autres classes dérivées de `CDC` encapsulent des fonctionnalités spécialisées de contexte de périphérique, y compris la prise en charge pour les métafichiers Windows.

[CDC](../mfc/reference/cdc-class.md)<br/>
La classe de base pour les contextes de périphérique. Utilisé directement pour accéder à l’affichage complet et pour accéder aux contextes de nondisplay tels que les imprimantes.

[CPaintDC](../mfc/reference/cpaintdc-class.md)<br/>
Utilisé dans un contexte d’affichage `OnPaint` fonctions membres de windows. Appelle automatiquement `BeginPaint` lors de la construction et `EndPaint` lors de la destruction.

[CClientDC](../mfc/reference/cclientdc-class.md)<br/>
Un contexte d’affichage pour les zones clientes de windows. Utilisé, par exemple, pour dessiner dans une réponse immédiate aux événements de souris.

[CWindowDC](../mfc/reference/cwindowdc-class.md)<br/>
Un contexte d’affichage pour windows entières, y compris les zones clientes et client.

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)<br/>
Un contexte de périphérique pour les métafichiers Windows. Un métafichier Windows contient une séquence de graphics device interface (GDI) commandes qui peuvent être relues pour créer une image. Les appels effectués aux fonctions membres d’un `CMetaFileDC` sont enregistrées dans un métafichier.

## <a name="related-classes"></a>Classes connexes

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Contient les paires de coordonnées (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Contient la distance positions relatives, valeurs ou associés.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Contient les coordonnées de zones rectangulaires.

[CRgn](../mfc/reference/crgn-class.md)<br/>
Encapsule une région GDI pour manipuler une zone polygonale, périodique ou elliptique dans une fenêtre. Utilisé conjointement avec les fonctions de membre de découpage dans la classe `CDC`.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Affiche et gère l’interface utilisateur pour le redimensionnement et le déplacement d’objets rectangulaires.

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
Fournit une boîte de dialogue standard permettant de sélectionner une couleur.

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour la sélection d’une police.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour l’impression d’un fichier.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
