---
title: Éléments de liste et listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: d378c6e07280349f9995981ad794039ebc015b25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353052"
---
# <a name="list-items-and-image-lists"></a>Éléments de liste et listes d'images

Un "élément" dans un contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)) se compose d’une icône, d’une étiquette, et peut-être d’autres informations (en "subitems").

Les icônes pour les éléments de contrôle de liste sont contenues dans les listes d’images. Une liste d’images contient des icônes grandeur nature utilisées en vue de l’icône. Une deuxième liste d’images facultative contient des versions plus petites des mêmes icônes pour une utilisation dans d’autres vues du contrôle. Une troisième liste facultative contient des images « d’état », telles que des cases à cocher, pour l’affichage devant les petites icônes dans certaines vues. Une quatrième liste facultative contient des images qui sont affichées dans les éléments d’en-tête individuels du contrôle de liste.

> [!NOTE]
> Si un contrôle de vue de liste est créé avec le style LVS_SHAREIMAGELISTS, vous êtes responsable de détruire les listes d’images lorsqu’elles ne sont plus utilisées. Spécifiez ce style si vous attribuez les mêmes listes d’images à plusieurs contrôles de vue de liste ; autrement, plus d’un contrôle pourrait essayer de détruire la même liste d’images.

Pour plus d’informations sur les éléments de liste, voir [Liste Afficher les listes d’images](/windows/win32/Controls/using-list-view-controls) et les éléments et [Subitems](/windows/win32/Controls/using-list-view-controls) dans le SDK Windows. Voir également la classe [CImageList](../mfc/reference/cimagelist-class.md) dans la *référence MFC* et [l’utilisation de CImageList](../mfc/using-cimagelist.md) dans cette famille d’articles.

Pour créer un contrôle de liste, vous devez fournir des listes d’images à utiliser lorsque vous insérez de nouveaux éléments dans la liste. L’exemple suivant montre cette procédure, où *m_pImagelist* `CImageList` est un pointeur `CListCtrl` de type et *m_listctrl* est un membre de données.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Toutefois, si vous n’avez pas l’intention d’afficher des icônes dans votre vue de liste ou contrôle de liste, vous n’avez pas besoin de listes d’images.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
