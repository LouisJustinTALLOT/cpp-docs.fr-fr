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
ms.openlocfilehash: e1ba9f29ebf2cb3b1f94620e815882c850bbc7cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213055"
---
# <a name="record-field-exchange-rfx"></a>Record Field Exchange (RFX)

Les classes de base de données ODBC MFC automatisent le déplacement de données entre la source de données et un objet [Recordset](../../data/odbc/recordset-odbc.md) . Lorsque vous dérivez une classe de [CRecordset](../../mfc/reference/crecordset-class.md) et que vous n’utilisez pas l’extraction de lignes en bloc, les données sont transférées par le mécanisme RFX (Record Field Exchange).

> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc dans une classe de `CRecordset` dérivée, le Framework utilise le mécanisme RFX en bloc pour transférer des données. Pour plus d’informations, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX est similaire à l’échange de données de boîtes de dialogue (DDX). Le déplacement de données entre une source de données et les données membres de champ d’un Recordset nécessite plusieurs appels à la fonction [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) du Recordset et une interaction considérable entre l’infrastructure et [ODBC](../../data/odbc/odbc-basics.md). Le mécanisme RFX est de type sécurisé et vous évite d’avoir à appeler des fonctions ODBC, telles que `::SQLBindCol`. Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

RFX est surtout transparent pour vous. Si vous déclarez vos classes de Recordset avec l’Assistant Application MFC ou **Ajoutez une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX est intégré automatiquement. Votre classe de Recordset doit être dérivée de la classe de base `CRecordset` fournie par le Framework. L’Assistant Application MFC vous permet de créer une classe de Recordset initiale. **Ajouter une classe** vous permet d’ajouter d’autres classes d’ensemble d’enregistrements en fonction de vos besoins. Pour plus d’informations et d’exemples, consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Vous devez ajouter manuellement une petite quantité de code RFX dans trois cas, lorsque vous souhaitez :

- Utilisez des requêtes paramétrables. Pour plus d’informations, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Effectuer des jointures (à l’aide d’un jeu d’enregistrements pour les colonnes de deux tables ou plus). Pour plus d’informations, consultez [Recordset : exécution d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Liaison dynamique des colonnes de données. Cela est moins courant que le paramétrage. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Si vous avez besoin d’une compréhension plus approfondie de RFX, consultez [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

Les rubriques suivantes expliquent les détails de l’utilisation des objets Recordset :

- [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Record Field Exchange : utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Consommation ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Prise en charge des bases de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)
