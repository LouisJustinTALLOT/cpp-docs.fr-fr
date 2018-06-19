---
title: Classes DAO | Documents Microsoft
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
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f43595ca5f688372a70999231ceebec5282cd3b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348920"
---
# <a name="dao-classes"></a>Classes DAO
Ces classes fonctionnent avec les autres classes application framework afin de donner un accès facile aux bases de données objet DAO (Data Access), qui utilisent le même moteur de base de données en tant que Microsoft Visual Basic et Microsoft Access. Les classes DAO peuvent également accéder à un large éventail de bases de données pour laquelle les pilotes de connectivité ODBC (Open Database) sont disponibles.  
  
 Les programmes qui utilisent des bases de données DAO aura au moins un `CDaoDatabase` objet et un `CDaoRecordset` objet.  
  
> [!NOTE]
>  Les Assistants et l’environnement Visual C++ plus en charge DAO (bien que les classes DAO sont incluses et vous pouvez toujours les utiliser). Microsoft recommande d’utiliser ODBC pour les nouveaux projets MFC. Vous devez uniquement utiliser DAO dans la maintenance des applications existantes.  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 Gère une session de base de données nommée et protégé par mot de passe de connexion à la fermeture de session. La plupart des programmes utilisent l’espace de travail par défaut.  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 Une connexion à une base de données par le biais duquel vous pouvez traiter les données.  
  
 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)  
 Représente un ensemble d'enregistrements sélectionnés à partir d'une source de données.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Vue qui affiche des enregistrements de base de données dans des contrôles.  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 Représente une définition de requête, généralement un enregistrement dans une base de données.  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 Représente la définition stockée d'une table de base ou d'une table attachée.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Représente une condition d’exception résultant des classes DAO.  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 Prend en charge les routines d'échange de champs d'enregistrements DAO (DFX) utilisées par les classes de base de données DAO. Vous utiliserez normalement pas directement cette classe.  
  
## <a name="related-classes"></a>Classes associées  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 Encapsule un handle vers le stockage pour un objet volumineux binaire (BLOB), par exemple une image bitmap. `CLongBinary` objets sont utilisés pour gérer les objets de grande quantité de données stockées dans des tables de base de données.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 Wrapper pour le type d’automatisation OLE **devise**, un type arithmétique à virgule fixe avec 15 chiffres avant la virgule décimale et 4 chiffres après.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Wrapper pour le type d’automatisation OLE **DATE**. Représente les valeurs de date et d’heure.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Wrapper pour le type d’automatisation OLE **variante**. Données de **VARIANT**s peuvent être stockées dans de nombreux formats.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

