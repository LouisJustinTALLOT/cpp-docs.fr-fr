---
title: Gestionnaires de commandes pour l’enregistrement de défilement (MFC Data Access) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03dec2e3eff0f61db5f4c8b7573400a589615b02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089377"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Gestionnaires de commandes pour le défilement des enregistrements (Accès aux données MFC)
Le [CRecordView](../mfc/reference/crecordview-class.md) classe fournit par défaut gestion des commandes pour les commandes standard suivantes :  
  
-   **ID_RECORD_MOVE_FIRST**  
  
-   **ID_RECORD_MOVE_LAST**  
  
-   **ID_RECORD_MOVE_NEXT**  
  
-   **ID_RECORD_MOVE_PREV**  
  
 Le `OnMove` fonction membre fournit par défaut gestion des commandes pour les quatre commandes, qui permettent de passer d’un enregistrement à l’autre. À mesure que ces commandes sont exécutées, RFX (ou DFX) charge le nouvel enregistrement dans les champs du recordset et DDX déplace les valeurs dans les contrôles du formulaire d'enregistrement. Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
> [!NOTE]
>  Veillez à utiliser ces ID de commandes standard pour tous les objets d'interface utilisateur associés aux commandes de navigation d'enregistrements standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de la Navigation dans une vue d’enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)