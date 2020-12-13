---
description: 'En savoir plus sur : schéma (accès aux données MFC)'
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
ms.openlocfilehash: 87080cb05d22a5328e0e6ad5a36b25771d319209
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332426"
---
# <a name="schema--mfc-data-access"></a>Schéma (Accès aux données MFC)

Un schéma de base de données décrit la structure actuelle des tables et des vues de base de données dans la base de données. En général, le code généré par l'Assistant part du principe que le schéma de la table ou des tables auxquelles un recordset accède ne changera pas, mais les classes de base de données peuvent gérer certaines modifications du schéma, telles que l'ajout, la réorganisation ou la suppression des colonnes non liées. Si une table change, vous devez mettre à jour le recordset  de la table manuellement, puis recompiler votre application.

Vous pouvez également compléter le code généré par l'Assistant pour gérer une base de données dont le schéma n'est pas entièrement connu au moment de la compilation. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Voir aussi

[Programmation de l’accès aux données (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Recordset (ODBC)](../data/odbc/recordset-odbc.md)
