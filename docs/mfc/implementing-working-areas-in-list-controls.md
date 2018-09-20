---
title: Implémentation d’espaces de travail dans les contrôles de liste | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc245ef87343d9f33277e41c5c191ea713e21da0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383413"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implémentation d'espaces de travail dans des contrôles de liste

Par défaut, un contrôle de liste réorganise tous les éléments sous forme de grille standard. Toutefois, une autre méthode est prise en charge, à savoir les zones de travail qui réorganisent les éléments de liste en groupes rectangulaires. Pour une image d’un contrôle de liste qui implémente des zones de travail, consultez l’aide de contrôles de mode liste dans le SDK Windows.

> [!NOTE]
>  Les zones de travail sont visibles uniquement lorsque le contrôle de liste est en mode icône ou petite icône. Toutefois, les zones de travail actives sont conservées si la vue passe en mode de rapport ou de liste.

Les zones de travail peuvent être utilisées pour afficher une bordure vide (à gauche, en haut et/ou à droite des éléments), ou forcer l'affichage d'une barre de défilement horizontale lorsqu'il n'y en a pas normalement. Une autre utilisation courante consiste à créer plusieurs zones de travail dans lesquelles des éléments peuvent être déplacés ou supprimés. Avec cette méthode, vous pouvez créer des zones dans une vue unique avec différentes significations. L'utilisateur peut ensuite classer les éléments en les plaçant dans une autre zone. La vue d'un système de fichiers avec une zone pour les fichiers en lecture/écriture et une autre zone pour les fichiers en lecture seule en est un exemple. Si un élément de fichier a été déplacé dans la zone en lecture seule, il passe automatiquement en lecture seule. Le déplacement d'un fichier de la zone en lecture seule vers la zone en lecture/écriture rend le fichier accessible en lecture/écriture.

`CListCtrl` fournit plusieurs fonctions membres pour créer et gérer les zones de travail dans votre contrôle de liste. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) et [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) récupérer et définir un tableau de `CRect` objets (ou `RECT` structures), qui stocke les zones de travail actuellement implémentées pour votre contrôle de liste. En outre, [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) récupère le nombre actuel de zones de travail pour votre contrôle de liste (par défaut, zéro).

## <a name="items-and-working-areas"></a>Éléments et zones de travail

Lorsqu'une zone de travail est créée, les éléments qui s'y trouvent en deviennent membres. De même, si un élément est déplacé dans une zone de travail, il devient membre de la zone de travail dans laquelle il a été déplacé. Si un élément ne se trouve dans aucune zone de travail, il devient automatiquement membre de la première zone de travail (index 0). Si vous souhaitez créer un élément et le placer dans un espace de travail spécifique, vous devez créer l’élément et puis le déplacer dans l’espace de travail souhaitée par un appel à [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Le deuxième exemple ci-dessous montre cette technique.

L'exemple suivant implémente quatre zones de travail (`rcWorkAreas`), de taille égale avec une bordure de 10 pixels de large autour de chacune d'elles, dans un contrôle de liste (`m_WorkAreaListCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

L’appel à [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) a été effectuée pour obtenir une estimation de la zone totale requise pour afficher tous les éléments dans une région. Cette estimation est ensuite divisée en quatre zones et complétée par une bordure de 5 pixels de large.

L’exemple suivant affecte les éléments de liste existants à chaque groupe (`rcWorkAreas`) et actualise l’affichage de contrôle (`m_WorkAreaListCtrl`) pour compléter l’effet.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

