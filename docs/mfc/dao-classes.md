---
title: Classes DAO
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 7ae85cbeb7790cadb8c26dfbdb7a5163dbcd47c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373520"
---
# <a name="dao-classes"></a>Classes DAO

DAO est utilisé avec les bases de données Access et est pris en charge par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète.

Ces classes fonctionnent avec les autres classes-cadres d’application pour faciliter l’accès aux bases de données des objets d’accès aux données (DAO), qui utilisent le même moteur de base de données que Microsoft Visual Basic et Microsoft Access. Les classes DAO peuvent également accéder à une grande variété de bases de données pour lesquelles les pilotes Open Database Connectivity (ODBC) sont disponibles.

Les programmes qui utilisent les bases `CDaoDatabase` de données `CDaoRecordset` DAO auront au moins un objet et un objet.

> [!NOTE]
> L’environnement visuel et les assistants ne prennent plus en charge DAO (bien que les classes DAO soient incluses et que vous puissiez toujours les utiliser). Microsoft vous recommande d’utiliser ODBC pour de nouveaux projets MFC. Vous ne devez utiliser DAO que pour maintenir les applications existantes.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Gère une session de base de données nommée, protégée par mot de passe, de la connexion au logoff. La plupart des programmes utilisent l’espace de travail par défaut.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Une connexion à une base de données par laquelle vous pouvez opérer sur les données.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Représente un ensemble d'enregistrements sélectionnés à partir d'une source de données.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Vue qui affiche des enregistrements de base de données dans des contrôles.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Représente une définition de requête, généralement celle enregistrée dans une base de données.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Représente la définition stockée d'une table de base ou d'une table attachée.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Représente une condition d’exception résultant des classes DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Prend en charge les routines d'échange de champs d'enregistrements DAO (DFX) utilisées par les classes de base de données DAO. Normalement, vous n’utiliserez pas directement cette classe.

## <a name="related-classes"></a>Classes connexes

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Encapsule une poignée de stockage pour un gros objet binaire (BLOB), comme une bitmap. `CLongBinary`objets sont utilisés pour gérer les grands objets de données stockés dans les tables de base de données.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Emballage pour le type d’automatisation OLE **CURRENCY**, un type arithmétique à point fixe, avec 15 chiffres avant le point décimal et 4 chiffres après.

[COleDateTime (en anglais)](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Emballage pour le type d’automatisation OLE **DATE**. Représente les valeurs de date et d’heure.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Emballage pour le type d’automatisation OLE **VARIANT**. Les données de **VARIANT**peuvent être stockées dans de nombreux formats.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../mfc/class-library-overview.md)
