---
title: Classes DAO
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 506206517fb37755bffc5f3a49635f0899232452
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447014"
---
# <a name="dao-classes"></a>Classes DAO

DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.

Ces classes fonctionnent avec les autres classes de l’infrastructure d’application pour fournir un accès facile aux bases de données d’objets d’accès aux données (DAO) qui utilisent le même moteur de base de données que Microsoft Visual Basic et Microsoft Access. Les classes DAO peuvent également accéder à un large éventail de bases de données pour lesquelles des pilotes Open Database Connectivity (ODBC) sont disponibles.

Les programmes qui utilisent des bases de données DAO auront au moins un objet `CDaoDatabase` et un objet `CDaoRecordset`.

> [!NOTE]
>  L’environnement C++ visuel et les assistants ne prennent plus en charge DAO (bien que les classes DAO soient incluses et vous puissiez toujours les utiliser). Microsoft recommande d’utiliser ODBC pour les nouveaux projets MFC. Vous ne devez utiliser que DAO pour gérer les applications existantes.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Gère une session de base de données nommée et protégée par mot de passe de la connexion à la fermeture de session. La plupart des programmes utilisent l’espace de travail par défaut.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Connexion à une base de données par le biais de laquelle vous pouvez travailler sur les données.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Représente un ensemble d'enregistrements sélectionnés à partir d'une source de données.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Vue qui affiche des enregistrements de base de données dans des contrôles.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Représente une définition de requête, généralement un enregistrement dans une base de données.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Représente la définition stockée d'une table de base ou d'une table attachée.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Représente une condition d’exception résultant des classes DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Prend en charge les routines d'échange de champs d'enregistrements DAO (DFX) utilisées par les classes de base de données DAO. Normalement, vous n’utiliserez pas directement cette classe.

## <a name="related-classes"></a>Classes connexes

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Encapsule un handle vers le stockage pour un objet BLOB (Binary Large Object), tel qu’une image bitmap. les objets `CLongBinary` sont utilisés pour gérer les objets de données volumineux stockés dans les tables de base de données.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Wrapper pour la **devise**de type OLE Automation, un type arithmétique à virgule fixe, avec 15 chiffres avant la virgule décimale et 4 chiffres après.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Wrapper pour la **Date**de type OLE Automation. Représente les valeurs de date et d’heure.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Wrapper pour la **variante**de type OLE Automation. Les données de la **variante**peuvent être stockées dans de nombreux formats.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
