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
ms.openlocfilehash: 8630fab11728b0c0cd16eee5035df028a8382706
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032217"
---
# <a name="record-field-exchange-rfx"></a>Record Field Exchange (RFX)

Les classes de base de données ODBC MFC automatisent le déplacement de données entre la source de données et un [recordset](../../data/odbc/recordset-odbc.md) objet. Lorsque vous dérivez une classe de [CRecordset](../../mfc/reference/crecordset-class.md) et n’utilisez pas l’extraction de lignes en bloc, les données sont transférées par le mécanisme record field exchange (RFX).

> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc dans une dérivée `CRecordset` (classe), le framework utilise le mécanisme RFX en bloc (RFX) pour transférer des données. Pour plus d’informations, consultez [jeu d’enregistrements : Extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX est similaire à l’échange de données de boîtes de dialogue (DDX). Déplacement de données entre une source de données et les membres de données de champ d’un recordset nécessite plusieurs appels à l’ensemble d’enregistrements [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) et une interaction considérable entre l’infrastructure et [ODBC](../../data/odbc/odbc-basics.md). Le mécanisme RFX est de type sécurisé et vous épargne le travail de l’appel de fonctions ODBC comme `::SQLBindCol`. Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

RFX est essentiellement transparente pour vous. Si vous déclarez vos classes de jeu d’enregistrements avec l’Assistant Application MFC ou **ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX est intégré automatiquement. Votre classe de jeu d’enregistrements doit être dérivée de la classe de base `CRecordset` fournie par le framework. L’Assistant Application MFC vous permet de créer une classe de recordset initiale. **Ajouter une classe** vous permet d’ajouter d’autres classes de jeu d’enregistrements que vous en avez besoin. Pour plus d’informations et des exemples, consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Vous devez ajouter manuellement une petite quantité de code RFX dans trois cas, lorsque vous souhaitez :

- Utilisez des requêtes paramétrables. Pour plus d’informations, consultez [jeu d’enregistrements : Paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Effectuer des jointures (à l’aide d’un jeu d’enregistrements pour les colonnes à partir de deux ou plusieurs tables). Pour plus d’informations, consultez [jeu d’enregistrements : Création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Lier dynamiquement les colonnes de données. Cela est moins fréquentes que le paramétrage. Pour plus d’informations, consultez [jeu d’enregistrements : Liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Si vous avez besoin d’une plus grande maîtrise de RFX, consultez [Record Field Exchange : Fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

Les rubriques suivantes expliquent les détails d’utilisation des objets de jeu d’enregistrements :

- [Record Field Exchange : Utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Record Field Exchange : Utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Record Field Exchange : Fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC, consommation](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Prise en charge des bases de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)