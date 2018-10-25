---
title: Schéma (accès de données MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 597b3870dbfc70b6e1ac392a45491ee0f1804c2f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055422"
---
# <a name="schema--mfc-data-access"></a>Schéma (Accès aux données MFC)

Un schéma de base de données décrit la structure actuelle des tables et des vues de base de données dans la base de données. En général, le code généré par l'Assistant part du principe que le schéma de la table ou des tables auxquelles un recordset accède ne changera pas, mais les classes de base de données peuvent gérer certaines modifications du schéma, telles que l'ajout, la réorganisation ou la suppression des colonnes non liées. Si une table change, vous devez mettre à jour le recordset  de la table manuellement, puis recompiler votre application.

Vous pouvez également compléter le code généré par l'Assistant pour gérer une base de données dont le schéma n'est pas entièrement connu au moment de la compilation. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Voir aussi

[Accès aux données de programmation (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Recordset (ODBC)](../data/odbc/recordset-odbc.md)