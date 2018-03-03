---
title: Enregistrer des vues (MFC Data Access) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e698cad29405fce4b5a0d23e166217502753dc1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="record-views--mfc-data-access"></a>Vues d'enregistrements (Accès aux données MFC)
Cette section s’applique uniquement aux classes ODBC MFC. Pour plus d’informations sur les vues des enregistrements OLE DB, consultez [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) et [à l’aide des vues de l’enregistrement OLE DB](../data/oledb/using-ole-db-record-views.md).  
  
 Pour prendre en charge les applications d’accès aux données de formulaire, la bibliothèque de classes fournit la classe [CRecordView](../mfc/reference/crecordview-class.md). Une vue d’enregistrement est un objet de vue de formulaire dont les contrôles sont mappés directement aux données membres de champ d’un [recordset](../data/odbc/recordset-odbc.md) objet (et indirectement aux colonnes correspondantes dans une table sur la source de données ou le résultat de la requête). Comme sa classe de base [CFormView](../mfc/reference/cformview-class.md), `CRecordView` est basée sur une ressource de modèle de boîte de dialogue.  
  
## <a name="form-uses"></a>Utilisations des formulaires  
 Les formulaires sont utiles pour diverses tâches d'accès aux données :  
  
-   Saisie de données  
  
-   Exécution de l'analyse des données en lecture seule  
  
-   Mise à jour des données  
  
## <a name="further-reading-about-record-views"></a>Informations complémentaires sur les vues d'enregistrements  
 Le contenu de ces rubriques s'applique aux classes ODBC et DAO. Utilisez `CRecordView` pour ODBC et `CDaoRecordView` pour DAO.  
  
 Les rubriques traitées ici sont les suivantes :  
  
-   [Fonctionnalités des Classes d’affichage de l’enregistrement](../data/features-of-record-view-classes-mfc-data-access.md)  
  
-   [Échange de données pour les vues des enregistrements](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
-   [Votre rôle dans l’utilisation d’une vue d’enregistrement](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
-   [Conception et création d’une vue d’enregistrement](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
-   [À l’aide d’une vue d’enregistrement](../data/using-a-record-view-mfc-data-access.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation (MFC/ATL) d’accès aux données](../data/data-access-programming-mfc-atl.md)   
 [Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)