---
title: ODBC et MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
ms.openlocfilehash: 38a625c73a17ecae4d8adc61e8c56bc4bdda67f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320072"
---
# <a name="odbc-and-mfc"></a>ODBC et MFC

> [!NOTE]
> Pour utiliser les classes de base de données MFC, vous devez avoir le pilote ODBC approprié pour votre source de données. Le dernier pilote Microsoft ODBC pour SQL Server est [Microsoft ODBC Driver 13 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). La plupart des fournisseurs de bases de données fournissent un pilote ODBC pour Windows.

Ce sujet introduit les principaux concepts des classes de base de données de la bibliothèque de la Fondation Microsoft (MFC) basées sur l’ODBC et donne un aperçu de la façon dont les classes fonctionnent ensemble. Pour plus d’informations sur ODBC et MFC, voir les sujets suivants :

- [Connexion à une source de données](connecting-to-a-data-source.md)

- [Sélection et manipulation d'enregistrements](selecting-and-manipulating-records.md)

- [Affichage et manipulation des données sous un formulaire](displaying-and-manipulating-data-in-a-form.md)

- [Travailler avec documents et points de vue](working-with-documents-and-views.md)

- [Accès à ODBC et SQL](access-to-odbc-and-sql.md)

- [Lire la suite des cours MFC ODBC](further-reading-about-the-mfc-odbc-classes.md)

Les classes de base de données MFC basées sur ODBC sont conçues pour donner accès à toute base de données pour laquelle un pilote ODBC est disponible. Étant donné que les classes utilisent ODBC, votre application peut accéder aux données dans de nombreux formats de données différents et différentes configurations locales/à distance. Vous n’avez pas besoin d’écrire un code de cas spécial pour gérer différents systèmes de gestion de base de données (DBMS). Tant que vos utilisateurs ont un pilote ODBC approprié pour les données qu’ils veulent accéder, ils peuvent utiliser votre programme pour manipuler les données dans les tables stockées là.)

## <a name="see-also"></a>Voir aussi

[Connectivité open Database (ODBC)](open-database-connectivity-odbc.md)
