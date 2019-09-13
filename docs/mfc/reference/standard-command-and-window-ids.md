---
title: ID de fenêtre et commande standard
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: 40783bc19e51afb0e9fe9e4a429df0239a8e7f09
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907715"
---
# <a name="standard-command-and-window-ids"></a>ID de fenêtre et commande standard

Le bibliothèque MFC (Microsoft Foundation Class) définit un certain nombre d’ID de commande et de fenêtre standard dans AFXRES. h. Ces ID sont le plus souvent utilisés dans les éditeurs de ressources et l' [Assistant classe](mfc-class-wizard.md) pour mapper les messages à vos fonctions gestionnaires. Toutes les commandes standard ont un préfixe **ID_** . Par exemple, lorsque vous utilisez l’éditeur de menus, vous liez normalement l’élément de menu ouvrir le fichier à l’ID de commande standard ID_FILE_OPEN.

Pour la plupart des commandes standard, le code d’application n’a pas besoin de faire référence à l’ID de commande, car l’infrastructure elle-même gère les commandes`CWinThread`via des tables `CDocument`de messages dans ses classes d’infrastructure principales (, `CWinApp`, `CView`, et ainsi de suite).

En plus des ID de commandes standard, un certain nombre d’ID standard sont définis et ont le préfixe **AFX_ID**. Ces ID incluent des ID de fenêtre standard (préfixe **AFX_IDW_** ), des ID de chaîne (préfixe **AFX_IDS_** ) et plusieurs autres types.

Les ID qui commencent par le préfixe **AFX_ID** sont rarement utilisés par les programmeurs, mais vous devrez peut-être faire référence à ces ID lors du remplacement des fonctions d’infrastructure qui font également référence aux **AFX_ID**s.

Les ID ne sont pas documentés individuellement dans cette référence. Vous trouverez plus d’informations sur ceux-ci dans les notes techniques [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md)et [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
>  Le fichier d’en-tête AFXRES. h est inclus indirectement dans AFXWIN. h. Vous devez inclure explicitement l’instruction suivante dans le fichier de script de ressources (. RC) de votre application :

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Voir aussi

[Macros et globales](../../mfc/reference/mfc-macros-and-globals.md)
