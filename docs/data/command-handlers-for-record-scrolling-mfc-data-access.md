---
title: Gestionnaires de commandes pour le défilement des enregistrements (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 66944221910dbd23d78a78fc951030efbee86bd0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038513"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Gestionnaires de commandes pour le défilement des enregistrements (Accès aux données MFC)

Le [CRecordView](../mfc/reference/crecordview-class.md) classe fournit par défaut gestion des commandes pour les commandes standards suivantes :

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

Le `OnMove` fonction membre fournit par défaut gestion des commandes pour les quatre commandes, qui permettent de passer d’un enregistrement à l’autre. À mesure que ces commandes sont exécutées, RFX (ou DFX) charge le nouvel enregistrement dans les champs du recordset et DDX déplace les valeurs dans les contrôles du formulaire d'enregistrement. Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
>  Veillez à utiliser ces ID de commandes standard pour tous les objets d'interface utilisateur associés aux commandes de navigation d'enregistrements standard.

## <a name="see-also"></a>Voir aussi

[Prise en charge de la navigation dans une vue de l'enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)