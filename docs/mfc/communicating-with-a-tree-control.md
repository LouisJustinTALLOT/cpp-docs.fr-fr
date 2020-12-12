---
description: 'En savoir plus sur : communication avec un contrôle d’arborescence'
title: Communication avec un contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: 82ee4fe0beb65e44166b4d68ffd44923b7fe0c76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310562"
---
# <a name="communicating-with-a-tree-control"></a>Communication avec un contrôle d'arborescence

Vous utilisez différentes méthodes pour appeler des fonctions membres dans un objet [CTreeCtrl](reference/ctreectrl-class.md) en fonction de la façon dont l’objet a été créé :

- Si le contrôle d’arborescence se trouve dans une boîte de dialogue, utilisez une variable membre de type `CTreeCtrl` que vous créez dans la classe de la boîte de dialogue.

- Si le contrôle d’arborescence est une fenêtre enfant, utilisez l' `CTreeCtrl` objet (ou pointeur) que vous avez utilisé pour construire l’objet.

- Si vous utilisez un `CTreeView` objet, utilisez la fonction [CTreeView :: GetTreeCtrl](reference/ctreeview-class.md#gettreectrl) pour obtenir une référence au contrôle d’arborescence. Vous pouvez initialiser une autre référence avec cette valeur ou assigner l’adresse de la référence à un `CTreeCtrl` pointeur.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](using-ctreectrl.md)<br/>
[Contrôles](controls-mfc.md)
