---
title: ODBC et les classes de base de données
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7c69f49cbe233eb0782fdaa9767ea55f4d04203c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213172"
---
# <a name="odbc-and-the-database-classes"></a>ODBC et les classes de base de données

Les classes de base de données ODBC MFC encapsulent les appels de fonction API ODBC que vous vous faites normalement dans les fonctions membres des classes [CDatabase](../../mfc/reference/cdatabase-class.md) et [CRecordset](../../mfc/reference/crecordset-class.md) . Par exemple, les classes de base de données gèrent les séquences d’appels ODBC complexes, la liaison des enregistrements retournés aux emplacements de stockage, la gestion des conditions d’erreur et d’autres opérations. Par conséquent, vous utilisez une interface de classe beaucoup plus simple pour manipuler des enregistrements à l’aide d’un objet Recordset.

> [!NOTE]
>  Les sources de données ODBC sont accessibles par le biais des classes ODBC MFC, comme décrit dans cette rubrique, ou par le biais des classes d’objets d’accès aux données (DAO) MFC.

Bien que les classes de base de données encapsulent les fonctionnalités ODBC, elles ne fournissent pas de mappage un-à-un des fonctions d’API ODBC. Les classes de base de données fournissent un niveau supérieur d’abstraction, modélisé après des objets d’accès aux données de Microsoft Access et Microsoft Visual Basic. Pour plus d’informations, consultez [ODBC et MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Voir aussi

[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)
