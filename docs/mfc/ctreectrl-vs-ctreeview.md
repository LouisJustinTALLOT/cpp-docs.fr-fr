---
description: 'En savoir plus sur les éléments suivants : CTreeCtrl et CTreeView'
title: CTreeCtrl comparé à CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: edaf2662d483a23c7618a143ee4aabe7910cf121
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309418"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl comparé à CTreeView

MFC fournit deux classes qui encapsulent les contrôles d’arborescence : [CTreeCtrl](reference/ctreectrl-class.md) et [CTreeView](reference/ctreeview-class.md). Chaque classe est utile dans différentes situations.

Utilisez `CTreeCtrl` lorsque vous avez besoin d’un contrôle de fenêtre enfant brut ; par exemple, dans une boîte de dialogue. Vous voudriez surtout utiliser `CTreeCtrl` s’il y a d’autres contrôles enfants dans la fenêtre, comme dans une boîte de dialogue classique.

Utilisez `CTreeView` lorsque vous souhaitez que le contrôle d’arborescence agisse comme une fenêtre d’affichage dans l’architecture document/vue, ainsi qu’un contrôle d’arborescence. Un `CTreeView` occupera la totalité de la zone client d’une fenêtre frame ou d’une fenêtre fractionnée. Elle est automatiquement redimensionnée lorsque sa fenêtre parente est redimensionnée et peut traiter les messages de commande à partir des menus, des touches accélérateur et des barres d’outils. Étant donné qu’un contrôle d’arborescence contient les données nécessaires pour afficher l’arborescence, l’objet document correspondant n’a pas besoin d’être compliqué. vous pouvez même utiliser [CDocument](reference/cdocument-class.md) comme type de document dans votre modèle de document.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](using-ctreectrl.md)<br/>
[Contrôles](controls-mfc.md)
