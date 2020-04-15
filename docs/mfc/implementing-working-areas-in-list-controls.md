---
title: Implémentation d'espaces de travail dans des contrôles de liste
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 91577203163247bd230fecb083cf1c50e2875b98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377225"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implémentation d'espaces de travail dans des contrôles de liste

Par défaut, un contrôle de liste réorganise tous les éléments sous forme de grille standard. Toutefois, une autre méthode est prise en charge, à savoir les zones de travail qui réorganisent les éléments de liste en groupes rectangulaires. Pour une image d’un contrôle de liste qui implémente les zones de travail, voir l’utilisation des contrôles List-View dans le SDK Windows.

> [!NOTE]
> Les zones de travail sont visibles uniquement lorsque le contrôle de liste est en mode icône ou petite icône. Toutefois, les zones de travail actives sont conservées si la vue passe en mode de rapport ou de liste.

Les zones de travail peuvent être utilisées pour afficher une bordure vide (à gauche, en haut et/ou à droite des éléments), ou forcer l'affichage d'une barre de défilement horizontale lorsqu'il n'y en a pas normalement. Une autre utilisation courante consiste à créer plusieurs zones de travail dans lesquelles des éléments peuvent être déplacés ou déposés. Avec cette méthode, vous pouvez créer des zones dans une vue unique avec différentes significations. L'utilisateur peut ensuite classer les éléments en les plaçant dans une autre zone. La vue d'un système de fichiers avec une zone pour les fichiers en lecture/écriture et une autre zone pour les fichiers en lecture seule en est un exemple. Si un élément de fichier a été déplacé dans la zone en lecture seule, il passe automatiquement en lecture seule. Le déplacement d'un fichier de la zone en lecture seule vers la zone en lecture/écriture rend le fichier accessible en lecture/écriture.

`CListCtrl` fournit plusieurs fonctions membres pour créer et gérer les zones de travail dans votre contrôle de liste. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) et [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) récupèrent `CRect` et mettent `RECT` en place une gamme d’objets (ou de structures), qui stockent les zones de travail actuellement mises en œuvre pour votre contrôle de liste. En outre, [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) récupère le nombre actuel de zones de travail pour votre contrôle de liste (par défaut, zéro).

## <a name="items-and-working-areas"></a>Éléments et zones de travail

Lorsqu'une zone de travail est créée, les éléments qui s'y trouvent en deviennent membres. De même, si un élément est déplacé dans une zone de travail, il devient membre de la zone de travail dans laquelle il a été déplacé. Si un élément ne se trouve dans aucune zone de travail, il devient automatiquement membre de la première zone de travail (index 0). Si vous souhaitez créer un élément et le placer dans une zone de travail spécifique, vous devrez créer l’élément, puis le déplacer dans la zone de travail désirée avec un appel à [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Le deuxième exemple ci-dessous montre cette technique.

L'exemple suivant implémente quatre zones de travail (`rcWorkAreas`), de taille égale avec une bordure de 10 pixels de large autour de chacune d'elles, dans un contrôle de liste (`m_WorkAreaListCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

L’appel à [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) a été fait pour obtenir une estimation de la superficie totale nécessaire pour afficher tous les éléments dans une région. Cette estimation est ensuite divisée en quatre zones et complétée par une bordure de 5 pixels de large.

L’exemple suivant attribue les éléments de`rcWorkAreas`liste existants à`m_WorkAreaListCtrl`chaque groupe ( ) et actualise la vue de contrôle ( ) pour compléter l’effet.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
