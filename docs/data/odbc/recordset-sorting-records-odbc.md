---
title: 'Recordset : Tri d’enregistrements (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ddb92016b7b911fc86f2feab27a698ce7fa55c45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090271"
---
# <a name="recordset-sorting-records-odbc"></a>Recordset : tri d'enregistrements (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique comment trier le jeu d’enregistrements. Vous pouvez spécifier une ou plusieurs colonnes sur laquelle baser le tri, et vous pouvez spécifier l’ordre croissant ou décroissant (`ASC` ou **DESC**; `ASC` est la valeur par défaut) pour chaque spécifiée de colonne. Par exemple, si vous spécifiez deux colonnes, les enregistrements sont triés d’abord sur la première colonne, puis sur la deuxième colonne nommée. SQL **ORDER BY** clause définit un tri. Lorsque le framework ajoute la **ORDER BY** clause to SQL du jeu d’enregistrements de requête, les contrôles de clause la sélection du classement.  
  
 Vous devez établir ordre de tri d’un jeu d’enregistrements après avoir construit l’objet mais avant d’appeler ses **ouvrir** fonction membre (ou avant d’appeler le **Requery** fonction membre d’un objet recordset existant dont **ouvrir** fonction membre a été appelée précédemment).  
  
#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Pour spécifier un ordre de tri pour un objet recordset  
  
1.  Construisez un nouvel objet recordset (ou préparez l’appel **Requery** pour un).  
  
2.  Définir la valeur de l’objet [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) membre de données.  
  
     Le tri est une chaîne se terminant par null. Il contient le contenu de la **ORDER BY** clause mais pas le mot clé **ORDER BY**. Par exemple, utilisez :  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  Définir d’autres options que vous avez besoin, telles que le mode de verrouillage, un filtre ou des paramètres.  
  
4.  Appelez **ouvrir** pour le nouvel objet (ou **Requery** pour un objet existant).  
  
 Les enregistrements sélectionnés sont classés comme spécifié. Par exemple, pour trier un ensemble d’enregistrements étudiant dans l’ordre décroissant par nom, puis du prénom, procédez comme suit :  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 Le jeu d’enregistrements contient tous les étudiants, triés par ordre décroissant (Z à A) par nom, puis par prénom.  
  
> [!NOTE]
>  Si vous choisissez de remplacer la chaîne SQL par défaut du jeu d’enregistrements en passant votre propre chaîne SQL à **ouvrir**, ne définissez pas de tri lorsque votre chaîne personnalisée contient une **ORDER BY** clause.  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)