---
title: Communication avec un contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: f480cdad2fce53f830b8067083a8a4be4b4e4848
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619648"
---
# <a name="communicating-with-a-tree-control"></a>Communication avec un contrôle d'arborescence

Vous utilisez différentes méthodes pour appeler des fonctions membres dans un objet [CTreeCtrl](reference/ctreectrl-class.md) en fonction de la façon dont l’objet a été créé :

- Si le contrôle d’arborescence se trouve dans une boîte de dialogue, utilisez une variable membre de type `CTreeCtrl` que vous créez dans la classe de la boîte de dialogue.

- Si le contrôle d’arborescence est une fenêtre enfant, utilisez l' `CTreeCtrl` objet (ou pointeur) que vous avez utilisé pour construire l’objet.

- Si vous utilisez un `CTreeView` objet, utilisez la fonction [CTreeView :: GetTreeCtrl](reference/ctreeview-class.md#gettreectrl) pour obtenir une référence au contrôle d’arborescence. Vous pouvez initialiser une autre référence avec cette valeur ou assigner l’adresse de la référence à un `CTreeCtrl` pointeur.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](using-ctreectrl.md)<br/>
[Commandes](controls-mfc.md)
