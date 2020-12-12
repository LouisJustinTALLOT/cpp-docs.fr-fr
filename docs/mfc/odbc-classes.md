---
description: 'En savoir plus sur : classes ODBC'
title: Classes ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: ac03543a6dfd9cf85320f9ff051730c102f2e0bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318687"
---
# <a name="odbc-classes"></a>Classes ODBC

Ces classes fonctionnent avec les autres classes de l’infrastructure d’application pour fournir un accès facile à un large éventail de bases de données pour lesquelles des pilotes Open Database Connectivity (ODBC) sont disponibles.

Les programmes qui utilisent des bases de données ODBC auront au moins un `CDatabase` objet et un `CRecordset` objet.

[CDatabase](reference/cdatabase-class.md)<br/>
Encapsule une connexion à une source de données, par l’intermédiaire de laquelle vous pouvez travailler sur la source de données.

[CRecordset](reference/crecordset-class.md)<br/>
Encapsule un ensemble d’enregistrements sélectionnés à partir d’une source de données. Les jeux d’enregistrements permettent de faire défiler un enregistrement vers un enregistrement, de mettre à jour des enregistrements (ajout, modification et suppression d’enregistrements), de qualifier la sélection à l’aide d’un filtre, de trier la sélection et de paramétrer la sélection avec les informations obtenues ou calculées au moment de l’exécution.

[CRecordView](reference/crecordview-class.md)<br/>
Fournit un mode formulaire directement connecté à un objet Recordset. Le mécanisme DDX (Dialog Data Exchange) échange des données entre le Recordset et les contrôles de la vue de l’enregistrement. Comme toutes les vues de formulaire, une vue d’enregistrement est basée sur une ressource de modèle de boîte de dialogue. Les vues d’enregistrement prennent également en charge le déplacement d’un enregistrement à un autre dans le jeu d’enregistrements, la mise à jour d’enregistrements et la fermeture du Recordset associé lorsque la vue d’enregistrement se ferme.

[CDBException](reference/cdbexception-class.md)<br/>
Exception résultant des échecs dans le traitement de l’accès aux données. Cette classe a le même objectif que d’autres classes d’exception dans le mécanisme de gestion des exceptions de la bibliothèque de classes.

[CFieldExchange](reference/cfieldexchange-class.md)<br/>
Fournit des informations de contexte pour prendre en charge RFX (Record Field Exchange), qui échange des données entre les membres de données de champ et les membres de données de paramètre d’un objet Recordset et les colonnes de table correspondantes sur la source de données. Similaire à la classe [CDataExchange](reference/cdataexchange-class.md), qui est utilisée de la même façon pour l’échange de données de boîtes de dialogue (DDX).

## <a name="related-classes"></a>Classes connexes

[CLongBinary](reference/clongbinary-class.md)<br/>
Encapsule un handle vers le stockage pour un objet BLOB (Binary Large Object), tel qu’une image bitmap. `CLongBinary` les objets sont utilisés pour gérer les objets de données volumineux stockés dans les tables de base de données.

[CDBVariant](reference/cdbvariant-class.md)<br/>
Vous permet de stocker une valeur sans vous préoccuper du type de données de la valeur. `CDBVariant` effectue le suivi du type de données de la valeur actuelle, qui est stockée dans une Union.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
