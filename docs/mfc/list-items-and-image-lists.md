---
title: Éléments de liste et listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 14abf72551d39b2d1b2069bd17da308b39d7f6cc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621403"
---
# <a name="list-items-and-image-lists"></a>Éléments de liste et listes d'images

Un « élément » dans un contrôle de liste ([CListCtrl](reference/clistctrl-class.md)) se compose d’une icône, d’une étiquette et éventuellement d’autres informations (dans des « sous-éléments »).

Les icônes des éléments de contrôle de liste sont contenues dans les listes d’images. Une liste d’images contient les icônes en taille réelle utilisées en mode icône. Une deuxième liste d’images, facultative, contient des versions plus petites des mêmes icônes pour une utilisation dans d’autres vues du contrôle. Une troisième liste facultative contient les images « État », telles que les cases à cocher, à afficher devant les petites icônes dans certains affichages. Une quatrième liste facultative contient des images affichées dans des éléments d’en-tête individuels du contrôle de liste.

> [!NOTE]
> Si un contrôle List View est créé avec le style LVS_SHAREIMAGELISTS, vous êtes responsable de la destruction des listes d’images lorsqu’elles ne sont plus utilisées. Spécifiez ce style si vous assignez les mêmes listes d’images à plusieurs contrôles d’affichage de liste. dans le cas contraire, plusieurs contrôles peuvent tenter de détruire la même liste d’images.

Pour plus d’informations sur les éléments de liste, consultez [listes d’images en mode liste](/windows/win32/Controls/using-list-view-controls) et [éléments et](/windows/win32/Controls/using-list-view-controls) sous-éléments dans le SDK Windows. Consultez également la classe [CImageList](reference/cimagelist-class.md) dans la *référence MFC* et [utilisation de CImageList](using-cimagelist.md) dans cette famille d’articles.

Pour créer un contrôle de liste, vous devez fournir des listes d’images à utiliser lorsque vous insérez de nouveaux éléments dans la liste. L’exemple suivant illustre cette procédure, où *m_pImagelist* est un pointeur de type `CImageList` et *m_listctrl* est un `CListCtrl` membre de données.

[!code-cpp[NVC_MFCControlLadenDialog#19](codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Toutefois, si vous n’envisagez pas d’afficher des icônes dans votre mode liste ou contrôle de liste, vous n’avez pas besoin de listes d’images.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](using-clistctrl.md)<br/>
[Commandes](controls-mfc.md)
