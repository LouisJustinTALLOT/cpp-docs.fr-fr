---
title: Classes ODBC
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: 75e022ea3e5de4a57f0ef2b1e3f312654c2889ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237773"
---
# <a name="odbc-classes"></a>Classes ODBC

Ces classes fonctionnent avec les autres classes de framework application afin de donner un accès facile à un large éventail de bases de données pour lesquelles les pilotes de connectivité ODBC (Open Database) sont disponibles.

Les programmes qui utilisent des bases de données ODBC ont au moins un `CDatabase` objet et un `CRecordset` objet.

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
Encapsule une connexion à une source de données, par le biais duquel vous pouvez utiliser la source de données.

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
Encapsule un ensemble d’enregistrements sélectionnés à partir d’une source de données. Jeux d’enregistrements activer le défilement d’un enregistrement à l’autre, la mise à jour des enregistrements (ajout, modification et suppression d’enregistrements), qualifier la sélection avec un filtre, le tri de la sélection et paramétrage de la sélection avec les informations fournies ou calculées au moment de l’exécution.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Fournit un formulaire de vue directement connectée à un objet recordset. Les données de la boîte de dialogue échangent mécanisme (DDX) échange des données entre le jeu d’enregistrements et les contrôles de la vue de l’enregistrement. Comme toutes les vues de formulaire, une vue d’enregistrement est basée sur une ressource de modèle de boîte de dialogue. Vues d’enregistrements prennent également en charge le déplacement d’un enregistrement à l’autre dans le jeu d’enregistrements, la mise à jour des enregistrements et fermer le jeu d’enregistrements lorsque la vue de l’enregistrement se ferme.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Une exception résultant d’échecs d’accès aux données du traitement. Cette classe remplit le même objectif que les autres classes d’exception dans le mécanisme de gestion des exceptions de la bibliothèque de classes.

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
Fournit des informations de contexte pour prendre en charge d’échange de champs d’enregistrements (RFX), qui échange des données entre les membres de données de champ et les membres de données de paramètre d’un objet de jeu d’enregistrements et les colonnes de table correspondantes sur la source de données. Analogue à la classe [CDataExchange](../mfc/reference/cdataexchange-class.md), qui est utilisé de la même manière pour l’échange de données de boîtes de dialogue (DDX).

## <a name="related-classes"></a>Classes connexes

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Encapsule un handle vers le stockage pour un objet binaire volumineux (BLOB), telles qu’une bitmap. `CLongBinary` objets sont utilisés pour gérer les objets de données volumineux stockés dans les tables de base de données.

[CDBVariant](../mfc/reference/cdbvariant-class.md)<br/>
vous permet de stocker une valeur sans se préoccuper du type de données. `CDBVariant` suit le type de données de la valeur actuelle, qui est stocké dans une union.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
