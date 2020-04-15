---
title: ODBC et les classes de base de données
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 6511aab9bb048882fe9c3398dd17f769eb16220c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320063"
---
# <a name="odbc-and-the-database-classes"></a>ODBC et les classes de base de données

Les classes de base de données MFC ODBC résument les appels de fonction API ODBC que vous feriez normalement vous-même dans les fonctions membres des classes [CDatabase](../../mfc/reference/cdatabase-class.md) et [CRecordset.](../../mfc/reference/crecordset-class.md) Par exemple, les séquences d’appels complexes d’ODBC, la liaison des enregistrements retournés aux emplacements de stockage, le traitement des conditions d’erreur et d’autres opérations sont gérés pour vous par les classes de base de données. En conséquence, vous utilisez une interface de classe considérablement plus simple pour manipuler des enregistrements à travers un objet de recordet.

> [!NOTE]
> Les sources de données de l’ODBC sont accessibles par l’intermédiaire des classes MFC ODBC, telles que décrites dans ce sujet, ou par l’intermédiaire des classes MFC Data Access Object (DAO).

Bien que les classes de base de données encapsulent la fonctionnalité ODBC, elles ne fournissent pas une cartographie en tête-à-tête des fonctions API d’ODBC. Les classes de base de données offrent un niveau plus élevé d’abstraction, calqué sur les objets d’accès aux données trouvés dans Microsoft Access et Microsoft Visual Basic. Pour plus d’informations, voir [ODBC et MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Voir aussi

[ODBC Basics](../../data/odbc/odbc-basics.md)
