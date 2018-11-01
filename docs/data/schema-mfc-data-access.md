---
title: Schéma (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
ms.openlocfilehash: 2dcfb5d22cf84fed7313686c943fbbd7c7ce1c84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512487"
---
# <a name="schema--mfc-data-access"></a>Schéma (Accès aux données MFC)

Un schéma de base de données décrit la structure actuelle des tables et des vues de base de données dans la base de données. En général, le code généré par l'Assistant part du principe que le schéma de la table ou des tables auxquelles un recordset accède ne changera pas, mais les classes de base de données peuvent gérer certaines modifications du schéma, telles que l'ajout, la réorganisation ou la suppression des colonnes non liées. Si une table change, vous devez mettre à jour le recordset  de la table manuellement, puis recompiler votre application.

Vous pouvez également compléter le code généré par l'Assistant pour gérer une base de données dont le schéma n'est pas entièrement connu au moment de la compilation. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Voir aussi

[Accès aux données de programmation (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Recordset (ODBC)](../data/odbc/recordset-odbc.md)