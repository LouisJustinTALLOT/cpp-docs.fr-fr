---
title: Classes DAO | Microsoft Docs
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
ms.openlocfilehash: c5af80f7a264a15f24ced0be37102802771dc6f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416680"
---
# <a name="dao-classes"></a>Classes DAO

Ces classes fonctionnent avec les autres classes de framework application afin de donner un accès facile aux bases de données objet DAO (Data Access), qui utilisent le même moteur de base de données en tant que Microsoft Visual Basic et Microsoft Access. Les classes DAO peuvent également accéder à un large éventail de bases de données pour lesquelles les pilotes de connectivité ODBC (Open Database) sont disponibles.

Les programmes qui utilisent des bases de données DAO aura au moins un `CDaoDatabase` objet et un `CDaoRecordset` objet.

> [!NOTE]
>  Les Assistants et l’environnement Visual C++ ne plus en charge DAO (bien que les classes DAO sont incluses et vous pouvez toujours les utiliser). Microsoft recommande d’utiliser ODBC pour les nouveaux projets MFC. Vous devez uniquement utiliser DAO à la gestion des applications existantes.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Gère une session de base de données nommée et protégé par mot de passe à partir de la connexion à la fermeture de session. La plupart des programmes utilisent l’espace de travail par défaut.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Une connexion à une base de données par le biais duquel vous pouvez traiter les données.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Représente un ensemble d'enregistrements sélectionnés à partir d'une source de données.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Vue qui affiche des enregistrements de base de données dans des contrôles.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Représente une définition de requête, généralement un enregistrement dans une base de données.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Représente la définition stockée d'une table de base ou d'une table attachée.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Représente une condition d’exception résultant des classes DAO de.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Prend en charge les routines d'échange de champs d'enregistrements DAO (DFX) utilisées par les classes de base de données DAO. Vous utiliserez normalement pas directement cette classe.

## <a name="related-classes"></a>Classes connexes

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Encapsule un handle vers le stockage pour un objet binaire volumineux (BLOB), telles qu’une bitmap. `CLongBinary` objets sont utilisés pour gérer les objets de données volumineux stockés dans les tables de base de données.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Wrapper pour le type d’automation OLE **devise**, un type arithmétique à virgule fixe, avec 15 chiffres avant la virgule décimale et 4 chiffres après.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Wrapper pour le type d’automation OLE **DATE**. Représente les valeurs de date et d’heure.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Wrapper pour le type d’automation OLE **VARIANT**. Données dans **VARIANT**s peuvent être stockées dans de nombreux formats.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

