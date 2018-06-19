---
title: Échange de données pour les vues des enregistrements (MFC Data Access) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 58bda2d9a712e38951b8201c08e5bbbe369537eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089413"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Échange de données pour les affichages des enregistrements (Accès aux données MFC)
Lorsque vous utilisez [ajouter une classe](../mfc/reference/adding-an-mfc-odbc-consumer.md) pour mapper les contrôles dans une ressource de modèle de boîte de dialogue d’une vue d’enregistrement aux champs d’un jeu d’enregistrements, l’infrastructure gère l’échange de données dans les deux sens : du recordset vers les contrôles et des contrôles vers le recordset. L'utilisation du mécanisme DDX signifie que vous n'êtes pas obligé d'écrire le code pour transférer les données d'une extrémité à une autre.  
  
 Le mécanisme DDX des vues des enregistrements fonctionne en association avec [RFX](../data/odbc/record-field-exchange-rfx.md) pour les recordsets de la classe `CRecordset` (ODBC).  RFX déplace les données entre l’enregistrement en cours de la source de données et les membres de données de champ d’un objet recordset. DDX déplace les données à partir des données membres de champ vers les contrôles dans le formulaire. Cette combinaison remplit les contrôles du formulaire initialement et à mesure que l'utilisateur passe d'un enregistrement à un autre. Elle peut également retransférer les données mises à jour vers le recordset, puis vers la source de données.  
  
 L’illustration suivante montre la relation entre DDX et RFX vues des enregistrements.  
  
 ![Boîte de dialogue&#45;échange de données et enregistrement&#45;champ exchange](../data/media/vc37xt1.gif "vc37xt1")  
Échange de données de boîtes de dialogue et de champs d'enregistrements  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues des enregistrements (MFC Data Access)](../data/record-views-mfc-data-access.md)   
 [Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)