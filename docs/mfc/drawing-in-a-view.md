---
title: Dessin dans une vue
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: 227c4614bad42706893301c69882c3f40af12e2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214342"
---
# <a name="drawing-in-a-view"></a>Dessin dans une vue

Presque tous les dessins de votre application se produisent dans la fonction membre `OnDraw` de la vue, que vous devez substituer dans votre classe d’affichage. (L’exception est le dessin de la souris, décrite dans interprétation de l' [entrée utilisateur via une vue](../mfc/interpreting-user-input-through-a-view.md).) Votre `OnDraw` remplacement :

1. Obtient les données en appelant les fonctions membres du document que vous fournissez.

1. Affiche les données en appelant les fonctions membres d’un objet de contexte d’appareil que le Framework passe à `OnDraw`.

Lorsque les données d’un document changent d’une certaine façon, la vue doit être redessinée pour refléter les modifications. En général, cela se produit lorsque l’utilisateur apporte une modification à l’aide d’une vue sur le document. Dans ce cas, la vue appelle la fonction membre [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) du document pour notifier toutes les vues du même document à se mettre à jour eux-mêmes. `UpdateAllViews` appelle la fonction membre [OnUpdate](../mfc/reference/cview-class.md#onupdate) de chaque vue. L’implémentation par défaut de `OnUpdate` invalide la zone cliente entière de la vue. Vous pouvez la remplacer pour invalider uniquement les régions de la zone cliente qui mappent aux parties modifiées du document.

La fonction membre `UpdateAllViews` de la classe `CDocument` et la fonction membre `OnUpdate` de la classe `CView` vous permettent de transmettre des informations décrivant les parties du document qui ont été modifiées. Ce mécanisme de « Conseil » vous permet de limiter la zone que la vue doit redessiner. `OnUpdate` prend deux arguments « hint ». Le premier, *lHint*, de type **lParam**, vous permet de passer toutes les données de votre choix, tandis que le second, *pHint*, de type `CObject`*, vous permet de passer un pointeur à n’importe quel objet dérivé de `CObject`.

Lorsqu’une vue n’est plus valide, Windows l’envoie un message de **WM_PAINT** . La fonction de gestionnaire [OnPaint](../mfc/reference/cwnd-class.md#onpaint) de la vue répond au message en créant un objet de contexte d’appareil de la classe [CPaintDC](../mfc/reference/cpaintdc-class.md) et appelle la fonction membre `OnDraw` de votre vue. Vous n’avez normalement pas besoin d’écrire une fonction de gestionnaire de `OnPaint` substituée.

Un [contexte de périphérique](../mfc/device-contexts.md) est une structure de données Windows qui contient des informations sur les attributs de dessin d’un appareil tel qu’un écran ou une imprimante. Tous les appels de dessin sont effectués à l’aide d’un objet de contexte d’appareil. Pour dessiner à l’écran, `OnDraw` reçoit un objet `CPaintDC`. Pour dessiner sur une imprimante, un objet [CDC](../mfc/reference/cdc-class.md) configuré pour l’imprimante actuelle lui est transmis.

Votre code pour dessiner dans la vue récupère d’abord un pointeur vers le document, puis effectue des appels de dessin via le contexte de périphérique. L’exemple de `OnDraw` simple suivant illustre le processus :

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

Dans cet exemple, vous devez définir la fonction `GetData` en tant que membre de votre classe de document dérivée.

L’exemple imprime toute chaîne qu’il obtient à partir du document, centrée dans la vue. Si le `OnDraw` appel est destiné au dessin à l’écran, l’objet `CDC` passé dans le *contrôleur de domaine principal* est un `CPaintDC` dont le constructeur a déjà appelé `BeginPaint`. Les appels aux fonctions de dessin sont effectués par le biais du pointeur de contexte de périphérique. Pour plus d’informations sur les contextes de périphérique et les appels de dessin, consultez la classe [CDC](../mfc/reference/cdc-class.md) dans la *référence MFC* et [utilisation d’objets de fenêtre](../mfc/working-with-window-objects.md).

Pour obtenir plus d’exemples d’écriture de `OnDraw`, consultez les [exemples MFC](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Voir aussi

[Utilisation de vues](../mfc/using-views.md)
