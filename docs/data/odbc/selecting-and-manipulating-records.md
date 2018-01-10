---
title: "Sélection et manipulation d’enregistrements | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dec5e0094405cf9d038e53959da97ba079736505
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-and-manipulating-records"></a>Sélection et manipulation d'enregistrements
Normalement lorsque vous sélectionnez des enregistrements à partir d’une source de données à l’aide de SQL **sélectionnez** instruction, vous obtenez un jeu de résultats, qui est un ensemble d’enregistrements à partir d’une table ou une requête. Avec les classes de base de données, vous utilisez un objet recordset pour sélectionner et accéder à l’ensemble de résultats. Il s’agit d’un objet d’une classe spécifique à l’application que vous dérivez de la classe [CRecordset](../../mfc/reference/crecordset-class.md). Lorsque vous définissez une classe de recordset, vous spécifiez la source de données à associer à la table à utiliser et les colonnes de la table. L’Assistant Application MFC ou **ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) crée une classe avec une connexion à une source de données spécifique. Les Assistants écrivent la [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) fonction membre de classe `CRecordset` pour retourner le nom de la table. Pour plus d’informations sur l’utilisation des Assistants pour créer des classes de jeu d’enregistrements, consultez [prise en charge de la base de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md) et [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 À l’aide un [CRecordset](../../mfc/reference/crecordset-class.md) de l’objet en cours d’exécution, vous pouvez :  
  
-   Examinez les champs de données de l’enregistrement actif.  
  
-   Filtrer ou trier le jeu d’enregistrements.  
  
-   Personnaliser la valeur par défaut SQL **sélectionnez** instruction.  
  
-   Faites défiler les enregistrements sélectionnés.  
  
-   Ajouter, mettre à jour ou supprimer des enregistrements (si la source de données et le jeu d’enregistrements sont modifiables).  
  
-   Tester si le jeu d’enregistrements permet d’effectuer de nouvelles requêtes et actualiser le contenu du recordset.  
  
 Lorsque vous avez terminé à l’aide de l’objet recordset, vous fermez et détruisez. Pour plus d’informations sur les jeux d’enregistrements, consultez [Recordset (ODBC)](../../data/odbc/recordset-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC et MFC](../../data/odbc/odbc-and-mfc.md)