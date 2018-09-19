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
ms.openlocfilehash: 7ff1759203593cd556a91cbe17b93388488a2b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091242"
---
# <a name="schema--mfc-data-access"></a>Schéma (Accès aux données MFC)

Un schéma de base de données décrit la structure actuelle des tables et des vues de base de données dans la base de données. En général, le code généré par l'Assistant part du principe que le schéma de la table ou des tables auxquelles un recordset accède ne changera pas, mais les classes de base de données peuvent gérer certaines modifications du schéma, telles que l'ajout, la réorganisation ou la suppression des colonnes non liées. Si une table change, vous devez mettre à jour le recordset  de la table manuellement, puis recompiler votre application.  
  
Vous pouvez également compléter le code généré par l'Assistant pour gérer une base de données dont le schéma n'est pas entièrement connu au moment de la compilation. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  

[Accès aux données de programmation (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Recordset (ODBC)](../data/odbc/recordset-odbc.md)