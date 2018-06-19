---
title: 'Exemple de relation contenant-contenu de Document actif : classeur Office | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7e4f82840a4c5620762ad57b5b9fa8dd7e62d0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345958"
---
# <a name="example-of-active-document-containment-office-binder"></a>Exemple de relation contenant-contenu de documents actifs : classeur Office
Le classeur Microsoft Office est un exemple d’un conteneur de documents actifs. Un classeur Office comprend deux volets principaux, comme conteneurs. Le volet gauche contient des icônes qui correspondent à des documents actifs dans le classeur. Chaque document est appelé un *section* dans le classeur. Par exemple, un classeur peut contenir des documents Word, PowerPoint fichiers, feuilles de calcul Excel et ainsi de suite.  
  
 En cliquant sur une icône dans le volet gauche Active le document actif correspondant. Le volet droit du classeur affiche ensuite le contenu du document actif actuellement sélectionné.  
  
 Si vous ouvrez et activez un document Word dans un classeur, la barre de menus de Word et les barres d’outils apparaissent en haut du frame d’affichage, et vous pouvez modifier le contenu du document à l’aide d’une commande de Word ou d’un outil. Toutefois, la barre de menus est une combinaison des barres de menus du classeur et de Word. Étant donné que le classeur et Word disposent **aide** fusion de menus, le contenu des menus respectifs. Fournissent automatiquement des conteneurs de documents actifs tels que le classeur Office **aide** menu fusion ; pour plus d’informations, consultez [la fusion de menus aide](../mfc/help-menu-merging.md).  
  
 Lorsque vous sélectionnez un document actif d’un autre type d’application, modifications de l’interface du classeur pour prendre en charge que du type d’application du document actif. Par exemple, si un classeur contient une feuille de calcul Excel, vous observerez que les menus dans le classeur sont modifiés lorsque vous sélectionnez la section de la feuille de calcul Excel.  
  
 Bien entendu, il existe des autres types possibles de conteneurs en dehors des classeurs. L’Explorateur de fichiers utilise l’interface de deux volets classique dans lequel le volet gauche utilise un contrôle d’arborescence pour afficher une liste hiérarchique des répertoires dans un lecteur ou un réseau, alors que le volet droit affiche les fichiers contenus dans le répertoire actuellement sélectionné. Généralement, un type de navigateur Internet du conteneur (telles que Microsoft Internet Explorer), au lieu d’utiliser une interface à deux volets, a une seule image et permet la navigation à l’aide de liens hypertexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Documents actifs (contenance)](../mfc/active-document-containment.md)

