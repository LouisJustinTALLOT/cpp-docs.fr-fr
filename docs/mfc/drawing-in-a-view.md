---
description: 'En savoir plus sur : dessin dans une vue'
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
ms.openlocfilehash: b5d6b33d91f6a71048162078a926c5ad4336d6a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283405"
---
# <a name="drawing-in-a-view"></a>Dessin dans une vue

Presque tous les dessins de votre application se produisent dans la `OnDraw` fonction membre de la vue, que vous devez substituer dans votre classe d’affichage. (L’exception est le dessin de la souris, décrite dans interprétation de l' [entrée utilisateur via une vue](interpreting-user-input-through-a-view.md).) Votre `OnDraw` remplacement :

1. Obtient les données en appelant les fonctions membres du document que vous fournissez.

1. Affiche les données en appelant les fonctions membres d’un objet de contexte d’appareil que le Framework passe à `OnDraw` .

Lorsque les données d’un document changent d’une certaine façon, la vue doit être redessinée pour refléter les modifications. En général, cela se produit lorsque l’utilisateur apporte une modification à l’aide d’une vue sur le document. Dans ce cas, la vue appelle la fonction membre [UpdateAllViews](reference/cdocument-class.md#updateallviews) du document pour notifier toutes les vues du même document à se mettre à jour eux-mêmes. `UpdateAllViews` appelle la fonction membre [OnUpdate](reference/cview-class.md#onupdate) de chaque vue. L’implémentation par défaut de `OnUpdate` invalide la zone cliente entière de la vue. Vous pouvez la remplacer pour invalider uniquement les régions de la zone cliente qui mappent aux parties modifiées du document.

La `UpdateAllViews` fonction membre de la classe `CDocument` et la `OnUpdate` fonction membre de la classe `CView` vous permettent de transmettre des informations décrivant les parties du document qui ont été modifiées. Ce mécanisme de « Conseil » vous permet de limiter la zone que la vue doit redessiner. `OnUpdate` accepte deux arguments « hint ». Le premier, *lHint*, de type **lParam**, vous permet de passer toutes les données de votre choix, tandis que le second, *pHint*, de type `CObject` *, vous permet de passer un pointeur vers n’importe quel objet dérivé de `CObject` .

Lorsqu’une vue n’est plus valide, Windows l’envoie un message de **WM_PAINT** . La fonction de gestionnaire [OnPaint](reference/cwnd-class.md#onpaint) de la vue répond au message en créant un objet de contexte d’appareil de la classe [CPaintDC](reference/cpaintdc-class.md) et appelle la fonction membre de votre vue `OnDraw` . Vous n’avez normalement pas besoin d’écrire une fonction de gestionnaire de substitution `OnPaint` .

Un [contexte de périphérique](device-contexts.md) est une structure de données Windows qui contient des informations sur les attributs de dessin d’un appareil tel qu’un écran ou une imprimante. Tous les appels de dessin sont effectués à l’aide d’un objet de contexte d’appareil. Pour dessiner à l’écran, `OnDraw` est passé à un `CPaintDC` objet. Pour dessiner sur une imprimante, un objet [CDC](reference/cdc-class.md) configuré pour l’imprimante actuelle lui est transmis.

Votre code pour dessiner dans la vue récupère d’abord un pointeur vers le document, puis effectue des appels de dessin via le contexte de périphérique. L’exemple simple suivant `OnDraw` illustre le processus :

[!code-cpp[NVC_MFCDocView#1](codesnippet/cpp/drawing-in-a-view_1.cpp)]

Dans cet exemple, vous définissez la `GetData` fonction en tant que membre de votre classe de document dérivée.

L’exemple imprime toute chaîne qu’il obtient à partir du document, centrée dans la vue. Si l' `OnDraw` appel est destiné au dessin à l’écran, l' `CDC` objet passé dans le *contrôleur de domaine principal* est un `CPaintDC` dont le constructeur a déjà appelé `BeginPaint` . Les appels aux fonctions de dessin sont effectués par le biais du pointeur de contexte de périphérique. Pour plus d’informations sur les contextes de périphérique et les appels de dessin, consultez la classe [CDC](reference/cdc-class.md) dans la *référence MFC* et [utilisation d’objets de fenêtre](working-with-window-objects.md).

Pour obtenir plus d’exemples d’écriture `OnDraw` , consultez les [exemples MFC](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Voir aussi

[Utilisation des vues](using-views.md)
