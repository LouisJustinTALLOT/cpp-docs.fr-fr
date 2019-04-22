---
title: ODBC et les classes de base de données
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7692a8128e3dac97c9107e986f6698db76c22c58
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025988"
---
# <a name="odbc-and-the-database-classes"></a>ODBC et les classes de base de données

Les classes de base de données ODBC MFC encapsulent les appels de fonction API ODBC que vous effectueriez normalement vous-même dans le membre de fonctions de la [CDatabase](../../mfc/reference/cdatabase-class.md) et [CRecordset](../../mfc/reference/crecordset-class.md) classes. Par exemple, les séquences d’appel ODBC complexes, la liaison d’enregistrements retournés à des emplacements de stockage, de gestion des conditions d’erreur et d’autres opérations sont gérées pour vous par les classes de base de données. Par conséquent, vous utilisez une interface de classe beaucoup plus simple pour manipuler des enregistrements via un objet recordset.

> [!NOTE]
>  Sources de données ODBC sont accessibles via les classes ODBC MFC, comme décrit dans cette rubrique, ou via les classes de données Access objet DAO (MFC).

Bien que les classes de base de données encapsulent la fonctionnalité ODBC, elles ne fournissent pas un mappage des fonctions API ODBC. Les classes de base de données fournissent un niveau plus élevé d’abstraction, basé sur les objets d’accès aux données de Microsoft Access et Microsoft Visual Basic. Pour plus d’informations, consultez [ODBC et MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Voir aussi

[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)