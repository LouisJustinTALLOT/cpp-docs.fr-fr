---
title: Votre rôle dans l’utilisation d’une vue d’enregistrement (MFC Data Access) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e7a9d3fa7e828467e73c77736fb5643baf19660f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111092"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Votre rôle dans l'utilisation d'une vue de l'enregistrement (Accès aux données MFC)
Le tableau suivant montre ce que vous devez généralement faire pour travailler avec une vue d'enregistrement et ce que l'infrastructure effectue pour vous.  
  
### <a name="working-with-a-record-view-you-and-the-framework"></a>Utilisation d'une vue d'enregistrement : l'infrastructure et vous  
  
|Vous|L'infrastructure|  
|---------|-------------------|  
|Utiliser l'éditeur de boîte de dialogue Visual C++ pour concevoir le formulaire.|Crée une ressource de modèle de boîte de dialogue avec des contrôles.|  
|Utilisez le [Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md) pour créer des classes dérivées de [CRecordView](../mfc/reference/crecordview-class.md) et [CRecordset](../mfc/reference/crecordset-class.md).|Écrit les classes pour vous.|  
|Mapper les contrôles de vue d'enregistrement à des données membres de champ de recordset.|Fournit DDX entre les contrôles et les champs du recordset.|  
||Fournit des gestionnaires de commandes pour valeur par défaut **Move First**, **Move Last**, **Move Next**, et **Move Previous** les commandes de menus ou barre d’outils boutons.|  
||Met à jour les modifications apportées à la source de données.|  
|[Facultatif] Écrire du code pour remplir les zones de liste ou zones de liste déroulante ou d'autres contrôles avec des données à partir d'un second recordset.||  
|[Facultatif] Écrire du code pour les validations spéciales.||  
|[Facultatif] Écrire du code pour ajouter ou supprimer des enregistrements.||  
  
 La programmation basée sur formulaire n'est qu'une approche parmi d'autres de l'utilisation d'une base de données. Pour plus d’informations sur les applications utilisant une autre interface utilisateur, ou aucune interface utilisateur, consultez [MFC : utilisation de Classes de base de données avec des Documents et vues](../data/mfc-using-database-classes-with-documents-and-views.md) et [MFC : utilisation de Classes de base de données sans document et les vues](../data/mfc-using-database-classes-without-documents-and-views.md). Pour d’autres approches sur l’affichage des enregistrements de base de données, voir les classes [CListView](../mfc/reference/clistview-class.md) et [CTreeView](../mfc/reference/ctreeview-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues des enregistrements (MFC Data Access)](../data/record-views-mfc-data-access.md)   
 [Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)