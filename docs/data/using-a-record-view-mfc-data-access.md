---
title: Utilisation d'une vue de l'enregistrement (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 611ddfd755eec84d4f2572a50c18802f988c5c3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209025"
---
# <a name="using-a-record-view--mfc-data-access"></a>Utilisation d'une vue de l'enregistrement (Accès aux données MFC)

Cette rubrique explique comment personnaliser le code par défaut pour les vues d'enregistrements que l'Assistant écrit pour vous. En règle générale, vous souhaitez limiter la sélection des enregistrements à l’aide d’un [filtre](../data/odbc/recordset-filtering-records-odbc.md) ou de [paramètres](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), peut-être [Trier](../data/odbc/recordset-sorting-records-odbc.md) les enregistrements, personnaliser l’instruction SQL.

L’utilisation de `CRecordView` est très similaire à l’utilisation de [CFormView](../mfc/reference/cformview-class.md). L'approche de base consiste à utiliser la vue d'enregistrement pour afficher et éventuellement mettre à jour les enregistrements d'un seul recordset. Au-delà, vous souhaiterez peut-être également utiliser d’autres jeux d’enregistrements, comme indiqué dans [vues des enregistrements : remplissage d’une zone de liste à partir d’un second Recordset](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)
