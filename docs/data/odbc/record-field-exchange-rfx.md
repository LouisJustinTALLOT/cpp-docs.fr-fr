---
title: Record Field Exchange (RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: 6f965b90e1e0bbcfd3ad04bb5b40644d61050b2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367160"
---
# <a name="record-field-exchange-rfx"></a>Record Field Exchange (RFX)

Les classes de base de données MFC ODBC automatisent les données mobiles entre la source de données et un objet [de recordset.](../../data/odbc/recordset-odbc.md) Lorsque vous dérivez une classe de [CRecordset](../../mfc/reference/crecordset-class.md) et que vous n’utilisez pas d’aller chercher en vrac, les données sont transférées par le mécanisme d’échange de champs de disques (RFX).

> [!NOTE]
> Si vous avez mis en œuvre la chasse à la ligne en vrac dans une classe dérivée, `CRecordset` le cadre utilise le mécanisme d’échange de champs d’enregistrement en vrac (Bulk RFX) pour transférer des données. Pour plus d’informations, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX est similaire à l’échange de données de dialogue (DDX). Le transfert des données entre une source de données et les données sur le terrain des membres d’un jeu d’enregistrement nécessite de multiples appels vers la fonction [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) du document et une interaction considérable entre le cadre et [ODBC](../../data/odbc/odbc-basics.md). Le mécanisme RFX est sans danger de type et vous permet `::SQLBindCol`d’appeler les fonctions ODBC telles que . Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

RFX est pour la plupart transparent pour vous. Si vous déclarez vos cours de disques avec l’assistant d’application MFC ou **la classe Add** (comme décrit dans [l’ajout d’un consommateur MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX y est intégré automatiquement. Votre classe de documents doit être `CRecordset` dérivée de la classe de base fournie par le cadre. Le MFC Application Wizard vous permet de créer une classe de disques initiale. **Ajouter classe** vous permet d’ajouter d’autres classes de recordset que vous en avez besoin. Pour plus d’informations et d’exemples, voir [Ajouter un MFC ODBC Consumer](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Vous devez ajouter manuellement une petite quantité de code RFX dans trois cas, lorsque vous souhaitez :

- Utilisez des requêtes paramétrisées. Pour plus d’informations, voir [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Effectuer des jointures (à l’aide d’un jeu d’enregistrement pour les colonnes de deux tables ou plus). Pour plus d’informations, voir [Recordset: Performing a Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Lier les colonnes de données dynamiquement. C’est moins courant que la paramètre. Pour plus d’informations, voir [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Si vous avez besoin d’une compréhension plus avancée de RFX, voir [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

Les sujets suivants expliquent les détails de l’utilisation d’objets de records :

- [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Record Field Exchange : utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Voir aussi

[Connectivité open Database (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Consommation ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Support de base de données, Assistant d’application MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
