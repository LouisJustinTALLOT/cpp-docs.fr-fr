---
title: ID de fenêtre et commande standard
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: a7f9e37702c686e13379d4034be94949f92e5e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372959"
---
# <a name="standard-command-and-window-ids"></a>ID de fenêtre et commande standard

La Microsoft Foundation Class Library définit un certain nombre d’ID de commande et de fenêtre standard dans Afxres.h. Ces cartes d’ID sont le plus couramment utilisées dans les éditeurs de ressources et [l’assistant de classe](mfc-class-wizard.md) pour cartographier les messages à vos fonctions de gestionnaire. Toutes les commandes standard ont un préfixe **ID_.** Par exemple, lorsque vous utilisez l’éditeur de menu, vous liez normalement l’élément de menu File Open à l’ID de commande standard ID_FILE_OPEN.

Pour la plupart des commandes standard, le code d’application n’a pas besoin de se référer à`CWinThread` `CWinApp`l’ID de commande, parce que le cadre lui-même gère les commandes à travers les cartes de messages dans ses classes-cadres primaires ( , , `CView`, `CDocument`et ainsi de suite).

En plus des Œd de commande standard, un certain nombre d’autres IDENT standard sont définis qui ont un préfixe de **AFX_ID**. Ces cartes d’ID comprennent des cartes d’ID standard (préfixe **AFX_IDW_),** des ID à chaîne (préfixe **AFX_IDS_),** et plusieurs autres types.

Les DIU qui commencent par le préfixe **AFX_ID** sont rarement utilisés par les programmeurs, mais vous devrez peut-être vous référer à ces DIM lorsque les fonctions-cadres primordiales se réfèrent également à **l’AFX_ID**s.

Les DIU ne sont pas documentés individuellement dans cette référence. Vous pouvez trouver plus d’informations à leur sujet dans les notes techniques [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), et [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
> Le fichier d’en-tête Afxres.h est indirectement inclus dans Afxwin.h. Vous devez inclure explicitement la déclaration suivante dans le fichier de script de ressources (.rc) de votre demande :

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
