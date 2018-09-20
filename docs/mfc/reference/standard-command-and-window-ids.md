---
title: ID de fenêtre et commande standard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2106312bd83edc4a37c904e2ee87ce78acb82904
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379124"
---
# <a name="standard-command-and-window-ids"></a>ID de fenêtre et commande standard

La bibliothèque Microsoft Foundation Class définit un numéro d’ID de fenêtre et commande standard dans Afxres.h. Ces ID est plus couramment utilisé dans les éditeurs de ressources et la fenêtre Propriétés pour mapper des messages à vos fonctions gestionnaires. Toutes les commandes standards ont un **ID_** préfixe. Par exemple, lorsque vous utilisez l’éditeur de menus, vous normalement lier l’élément de menu Ouvrir le fichier à l’ID de commande ID_FILE_OPEN standard.

Pour la plupart des commandes, code d’application est inutile faire référence à l’ID de commande, car l’infrastructure elle-même gère les commandes via les tables des messages dans ses classes de framework principal (`CWinThread`, `CWinApp`, `CView`, `CDocument`, et ainsi de suite).

En plus de l’ID de commande standard, un nombre d’autres ID standard est défini qui ont un préfixe de **AFX_ID**. Ces ID inclure l’ID de fenêtre standard (préfixe **AFX_IDW_**), ID de chaîne (préfixe **AFX_IDS_**) et plusieurs autres types.

ID qui commencent par le **AFX_ID** préfixe sont rarement utilisés par les programmeurs, mais vous devrez peut-être faire référence à ces ID lors de la substitution des fonctions de framework également faire référence à la **AFX_ID**s.

Individuellement, les ID ne sont pas documentés dans cette référence. Vous trouverez plus d’informations sur ces derniers dans les Notes techniques [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), et [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
>  Le fichier d’en-tête Afxres.h est indirectement inclus dans Afxwin.h. Vous devez inclure explicitement l’instruction suivante dans le fichier de script (.rc) de ressources de votre application :

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
