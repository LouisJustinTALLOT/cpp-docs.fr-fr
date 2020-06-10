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
ms.openlocfilehash: fe9ccb5b78d9a60c5b8b2a19fe0818a8e1682f00
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623123"
---
# <a name="example-of-active-document-containment-office-binder"></a>Exemple de relation contenant-contenu de documents actifs : classeur Office

Le classeur Microsoft Office est un exemple de conteneur de documents actifs. Un classeur Office comprend deux volets principaux, comme le font les conteneurs. Le volet gauche contient des icônes qui correspondent aux documents actifs dans le classeur. Chaque document est appelé une *section* dans le classeur. Par exemple, un classeur peut contenir des documents Word, des fichiers PowerPoint, des feuilles de calcul Excel, etc.

Si vous cliquez sur une icône dans le volet gauche, le document actif correspondant est activé. Le volet droit du classeur affiche ensuite le contenu du document actif actuellement sélectionné.

Si vous ouvrez et activez un document Word dans un classeur, la barre de menus et les barres d’outils Word apparaissent en haut du frame de vue et vous pouvez modifier le contenu du document à l’aide de n’importe quelle commande ou n’importe quel outil Word. Toutefois, la barre de menus est une combinaison des barres de menus du Binder et de Word. Étant donné que Binder et Word ont des menus **d’aide** , le contenu des menus respectifs est fusionné. Les conteneurs de documents actifs tels que le classeur Office fournissent automatiquement une fusion du menu **aide** ; Pour plus d’informations, consultez [fusion du menu aide](help-menu-merging.md).

Lorsque vous sélectionnez un document actif d’un autre type d’application, l’interface du Binder change pour s’adapter à celle du type d’application du document actif. Par exemple, si un classeur contient une feuille de calcul Excel, vous remarquerez que les menus du classeur sont modifiés lorsque vous sélectionnez la section feuille de calcul Excel.

Il existe, bien sûr, d’autres types de conteneurs possibles en regard des classeurs. L’Explorateur de fichiers utilise l’interface classique à deux volets dans laquelle le volet gauche utilise un contrôle d’arborescence pour afficher une liste hiérarchique des répertoires dans un lecteur ou un réseau, tandis que le volet droit affiche les fichiers contenus dans le répertoire actuellement sélectionné. Un type de conteneur de navigateur Internet (tel que Microsoft Internet Explorer), au lieu d’utiliser une interface à deux volets, a généralement une seule image et permet de naviguer à l’aide de liens hypertexte.

## <a name="see-also"></a>Voir aussi

[Documents actifs (contenance)](active-document-containment.md)
