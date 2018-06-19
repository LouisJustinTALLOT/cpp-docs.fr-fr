---
title: Classes ODBC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98ef4509e7e7570d8c07013f0287fe01105e154a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348138"
---
# <a name="odbc-classes"></a>Classes ODBC
Ces classes fonctionnent avec les autres classes application framework afin de donner un accès facile à une grande variété de bases de données pour laquelle les pilotes de connectivité ODBC (Open Database) sont disponibles.  
  
 Les programmes qui utilisent des bases de données ODBC ont au moins un `CDatabase` objet et un `CRecordset` objet.  
  
 [CDatabase](../mfc/reference/cdatabase-class.md)  
 Encapsule une connexion à une source de données, par le biais duquel vous pouvez utiliser la source de données.  
  
 [CRecordset](../mfc/reference/crecordset-class.md)  
 Encapsule un ensemble d’enregistrements sélectionnés à partir d’une source de données. Jeux d’enregistrements activer le défilement d’un enregistrement à l’autre, la mise à jour des enregistrements (ajout, modification et suppression d’enregistrements), qualifier la sélection avec un filtre, le tri de la sélection et le paramétrage de la sélection des informations obtenues ou calculée au moment de l’exécution.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Fournit une forme vue directement connectée à un objet recordset. Mécanisme (DDX) échange des données entre le jeu d’enregistrements et les contrôles de la vue de l’enregistrement d’échange de données de la boîte de dialogue. Comme toutes les vues du formulaire, une vue d’enregistrement est basée sur une ressource de modèle de boîte de dialogue. Vues d’enregistrements prennent également en charge le déplacement entre les enregistrements dans le jeu d’enregistrements, enregistrements de mise à jour et fermer le jeu d’enregistrements la fermeture de la vue de l’enregistrement.  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 Une exception résultant des échecs d’accès aux données le traitement. Cette classe remplit le même objectif que les autres classes d’exception dans le mécanisme de gestion des exceptions de la bibliothèque de classes.  
  
 [CFieldExchange](../mfc/reference/cfieldexchange-class.md)  
 Fournit des informations de contexte pour prendre en charge d’échange de champs d’enregistrements (RFX), qui échange des données entre les membres de données de champ et les membres de données de paramètre d’un objet de jeu d’enregistrements et les colonnes de table correspondantes sur la source de données. Analogue à la classe [CDataExchange](../mfc/reference/cdataexchange-class.md), qui est utilisé de la même façon pour l’échange de données de boîtes de dialogue (DDX).  
  
## <a name="related-classes"></a>Classes associées  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 Encapsule un handle vers le stockage pour un objet volumineux binaire (BLOB), par exemple une image bitmap. `CLongBinary` objets sont utilisés pour gérer les objets de grande quantité de données stockées dans des tables de base de données.  
  
 [CDBVariant](../mfc/reference/cdbvariant-class.md)  
 Vous permet de stocker une valeur sans se préoccuper du type de données. `CDBVariant` effectue le suivi du type de données de la valeur actuelle, qui est stocké dans une union.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

