---
description: 'En savoir plus sur : connexion à une source de données'
title: Connexion à une source de données
ms.date: 11/04/2016
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
ms.openlocfilehash: 3bc5436a678d39682b89d82dd7f3ab90eb6f5bb5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295118"
---
# <a name="connecting-to-a-data-source"></a>Connexion à une source de données

Une source de données ODBC est un ensemble spécifique de données, les informations requises pour accéder à ces données et l’emplacement de la source de données, qui peut être décrit à l’aide d’un nom de source de données. Du point de vue de votre programme, la source de données comprend les données, le SGBD, le réseau (le cas échéant) et ODBC.

Pour accéder aux données fournies par une source de données, votre programme doit d’abord établir une connexion à la source de données. Tout l’accès aux données est géré par le biais de cette connexion.

Les connexions à la source de données sont encapsulées par la classe [CDatabase](../../mfc/reference/cdatabase-class.md). Quand un `CDatabase` objet est connecté à une source de données, vous pouvez :

- Construire des [jeux d’enregistrements](../../mfc/reference/crecordset-class.md), qui sélectionnent des enregistrements à partir de tables ou de requêtes.

- Gérez les [transactions](../../data/odbc/transaction-odbc.md), en regroupant les mises à jour afin que toutes soient validées à la source de données à la fois (ou que la transaction entière soit restaurée afin que la source de données soit inchangée), si la source de données prend en charge le niveau requis de transactions.

- Exécuter directement des instructions [SQL](../../data/odbc/sql.md) .

Lorsque vous avez terminé d’utiliser une connexion à la source de données, vous fermez l' `CDatabase` objet et vous le détruisez ou vous le réutilisez pour une nouvelle connexion. Pour plus d’informations sur les connexions à la source de données, consultez [source de données (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="see-also"></a>Voir aussi

[ODBC et MFC](../../data/odbc/odbc-and-mfc.md)
