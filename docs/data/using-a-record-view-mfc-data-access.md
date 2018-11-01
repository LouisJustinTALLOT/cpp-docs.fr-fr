---
title: Utilisation d'une vue de l'enregistrement (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: a051394fd79dfb84801a1fb9e700a7ce49ed1c7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605177"
---
# <a name="using-a-record-view--mfc-data-access"></a>Utilisation d'une vue de l'enregistrement (Accès aux données MFC)

Cette rubrique explique comment personnaliser le code par défaut pour les vues d'enregistrements que l'Assistant écrit pour vous. En règle générale, vous souhaitez contraindre la sélection d’enregistrement avec un [filtre](../data/odbc/recordset-filtering-records-odbc.md) ou [paramètres](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), par exemple [tri](../data/odbc/recordset-sorting-records-odbc.md) les enregistrements, personnaliser l’instruction SQL.

À l’aide de `CRecordView` est similaire à l’aide [CFormView](../mfc/reference/cformview-class.md). L'approche de base consiste à utiliser la vue d'enregistrement pour afficher et éventuellement mettre à jour les enregistrements d'un seul recordset. En outre, vous souhaiterez peut-être utiliser d’autres recordsets, comme indiqué dans [vues d’enregistrements : remplissage d’une zone de liste à partir d’un Second Recordset](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)