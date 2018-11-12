---
title: 'Exemple de relation contenant-contenu de documents actifs : classeur Office'
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
ms.openlocfilehash: 032b2cb39d75c108239d882039f7c797a357a6bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616648"
---
# <a name="example-of-active-document-containment-office-binder"></a>Exemple de relation contenant-contenu de documents actifs : classeur Office

Le classeur Microsoft Office est un exemple d’un conteneur de documents actifs. Un classeur Office comprend deux volets principaux, comme le font généralement conteneurs. Le volet gauche contient les icônes qui correspondent à des documents actifs dans le classeur. Chaque document est appelé un *section* dans le classeur. Par exemple, un classeur peut contenir des documents Word, PowerPoint fichiers, des feuilles de calcul Excel et ainsi de suite.

En cliquant sur une icône dans le volet gauche Active le document actif correspondant. Le volet droit du classeur affiche ensuite le contenu du document actif actuellement sélectionné.

Si vous ouvrez et activez un document Word dans un classeur, la barre de menus de Word et les barres d’outils apparaissent en haut de la frame de vue, et vous pouvez modifier le contenu du document à l’aide de n’importe quel outil ou une commande de Word. Toutefois, la barre de menus est une combinaison des barres de menus du classeur et de Word. Étant donné que le classeur et Word disposent **aide** les menus, le contenu des menus respectifs sont fusionnés. Fournissent automatiquement des conteneurs de documents actifs tels que le classeur Office **aide** menu fusion ; pour plus d’informations, consultez [vous aider à la fusion de menus](../mfc/help-menu-merging.md).

Lorsque vous sélectionnez un document actif d’un autre type d’application, modifications de l’interface du classeur pour prendre en charge que du type d’application du document actif. Par exemple, si un classeur contient une feuille de calcul Excel, vous observerez que les menus dans le classeur changent lorsque vous sélectionnez la section de la feuille de calcul Excel.

Bien sûr, il existe des autres types possibles de conteneurs en dehors des classeurs. Explorateur de fichiers utilise l’interface de deux volets classique dans lequel le volet gauche utilise un contrôle d’arborescence pour afficher une liste hiérarchique des répertoires dans un lecteur ou un réseau, tandis que le volet droit affiche les fichiers contenus dans le répertoire actuellement sélectionné. Généralement, un type de navigateur Internet de conteneur (par exemple, Microsoft Internet Explorer), plutôt qu’à l’aide d’une interface à deux volets, a une seule image et assure la navigation à l’aide de liens hypertexte.

## <a name="see-also"></a>Voir aussi

[Documents actifs (contenance)](../mfc/active-document-containment.md)

