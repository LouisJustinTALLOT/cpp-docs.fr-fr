---
description: 'En savoir plus sur : ODBC et les classes de base de données'
title: ODBC et les classes de base de données
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 146170ddd97dfc2797fd1f755459f370be638ded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326768"
---
# <a name="odbc-and-the-database-classes"></a>ODBC et les classes de base de données

Les classes de base de données ODBC MFC encapsulent les appels de fonction API ODBC que vous vous faites normalement dans les fonctions membres des classes [CDatabase](../../mfc/reference/cdatabase-class.md) et [CRecordset](../../mfc/reference/crecordset-class.md) . Par exemple, les classes de base de données gèrent les séquences d’appels ODBC complexes, la liaison des enregistrements retournés aux emplacements de stockage, la gestion des conditions d’erreur et d’autres opérations. Par conséquent, vous utilisez une interface de classe beaucoup plus simple pour manipuler des enregistrements à l’aide d’un objet Recordset.

> [!NOTE]
> Les sources de données ODBC sont accessibles par le biais des classes ODBC MFC, comme décrit dans cette rubrique, ou par le biais des classes d’objets d’accès aux données (DAO) MFC.

Bien que les classes de base de données encapsulent les fonctionnalités ODBC, elles ne fournissent pas de mappage un-à-un des fonctions d’API ODBC. Les classes de base de données fournissent un niveau supérieur d’abstraction, modélisé après des objets d’accès aux données de Microsoft Access et Microsoft Visual Basic. Pour plus d’informations, consultez [ODBC et MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Voir aussi

[Notions de base relatives à ODBC](../../data/odbc/odbc-basics.md)
