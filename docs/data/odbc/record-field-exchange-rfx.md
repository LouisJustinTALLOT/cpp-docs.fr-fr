---
title: Record Field Exchange (RFX) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b214cf05115056efc96c4a078dedd4b7f9a3a1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091652"
---
# <a name="record-field-exchange-rfx"></a>Record Field Exchange (RFX)
Les classes de base de données ODBC MFC automatisent le transfert de données entre la source de données et un [recordset](../../data/odbc/recordset-odbc.md) objet. Lorsque vous dérivez une classe à partir de [CRecordset](../../mfc/reference/crecordset-class.md) et n’utilisez pas l’extraction de lignes en bloc, les données sont transférées par le mécanisme de record field exchange (RFX).  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc dans une dérivée `CRecordset` (classe), l’infrastructure utilise le mécanisme RFX en bloc (RFX) pour transférer des données. Pour plus d’informations, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 RFX est similaire à l’échange de données de boîtes de dialogue (DDX). Déplacement de données entre une source de données et les membres de données de champ d’un jeu d’enregistrements nécessite plusieurs appels à l’ensemble d’enregistrements [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) et une importante interaction entre l’infrastructure et [ODBC](../../data/odbc/odbc-basics.md). Le mécanisme RFX est de type sécurisé et vous épargne le travail de l’appel de fonctions ODBC comme **:: SQLBindCol**. Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
 RFX principalement est transparent pour l’utilisateur. Si vous déclarez vos classes de jeu d’enregistrements avec l’Assistant Application MFC ou **ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX est intégré automatiquement. La classe de recordset doit être dérivée de la classe de base `CRecordset` fourni par l’infrastructure. L’Assistant Application MFC permet de créer une classe de recordset initiale. **Ajouter une classe** vous permet d’ajouter d’autres classes de jeu d’enregistrements dont vous avez besoin. Pour plus d’informations et d’exemples, consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Vous devez ajouter manuellement une petite quantité de code RFX dans trois cas, lorsque vous souhaitez :  
  
-   Utiliser des requêtes paramétrables. Pour plus d’informations, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
-   Effectuer des jointures (à l’aide d’un jeu d’enregistrements pour les colonnes à partir de deux tables ou plus). Pour plus d’informations, consultez [Recordset : création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
-   Lier dynamiquement des colonnes de données. Cela est moins fréquent que le paramétrage. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Si vous avez besoin d’une plus grande maîtrise de RFX, consultez [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 Les rubriques suivantes expliquent en détail l’utilisation des objets de jeu d’enregistrements :  
  
-   [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [Record Field Exchange : utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [MFC ODBC, consommation](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Prise en charge de base de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [CRecordset, classe](../../mfc/reference/crecordset-class.md)