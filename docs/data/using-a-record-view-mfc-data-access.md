---
title: À l’aide d’une vue d’enregistrement (MFC Data Access) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23dd3335f6c77a3efec26f13e78824806f05821a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104641"
---
# <a name="using-a-record-view--mfc-data-access"></a>Utilisation d'une vue de l'enregistrement (Accès aux données MFC)
Cette rubrique explique comment personnaliser le code par défaut pour les vues d'enregistrements que l'Assistant écrit pour vous. En règle générale, vous souhaitez contraindre la sélection d’enregistrement avec un [filtre](../data/odbc/recordset-filtering-records-odbc.md) ou [paramètres](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), par exemple [tri](../data/odbc/recordset-sorting-records-odbc.md) les enregistrements, personnaliser l’instruction SQL.  
  
 À l’aide de `CRecordView` est similaire à l’aide [CFormView](../mfc/reference/cformview-class.md). L'approche de base consiste à utiliser la vue d'enregistrement pour afficher et éventuellement mettre à jour les enregistrements d'un seul recordset. En outre, vous souhaiterez peut-être utiliser d’autres recordsets, comme expliqué dans [vues des enregistrements : remplissage d’une zone de liste à partir d’un Second Recordset](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues des enregistrements (MFC Data Access)](../data/record-views-mfc-data-access.md)   
 [Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)