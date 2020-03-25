---
title: Gestionnaires de commandes pour le défilement des enregistrements (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 8bbacd6625e846381d2bafc8133e8b36efe51b1a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213445"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Gestionnaires de commandes pour le défilement des enregistrements (Accès aux données MFC)

La classe [CRecordView](../mfc/reference/crecordview-class.md) fournit la gestion des commandes par défaut pour les commandes standard suivantes :

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

La fonction membre `OnMove` fournit la gestion des commandes par défaut pour les quatre commandes, qui se déplacent d’un enregistrement à l’autre. À mesure que ces commandes sont exécutées, RFX (ou DFX) charge le nouvel enregistrement dans les champs du recordset et DDX déplace les valeurs dans les contrôles du formulaire d'enregistrement. Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
>  Veillez à utiliser ces ID de commandes standard pour tous les objets d'interface utilisateur associés aux commandes de navigation d'enregistrements standard.

## <a name="see-also"></a>Voir aussi

[Prise en charge de la navigation dans une vue d’enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
