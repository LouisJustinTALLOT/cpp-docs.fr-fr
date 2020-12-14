---
description: 'En savoir plus sur les éléments suivants : ODBC et MFC'
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
ms.openlocfilehash: 32cc3f9a023a4b965e8872fde27291bf8df3f1a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195097"
---
# <a name="odbc-and-mfc"></a>ODBC et MFC

> [!NOTE]
> Pour utiliser les classes de base de données MFC, vous devez disposer du pilote ODBC approprié pour votre source de données. Le dernier pilote Microsoft ODBC pour SQL Server est [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). La plupart des fournisseurs de bases de données fournissent un pilote ODBC pour Windows.

Cette rubrique présente les principaux concepts des classes de base de données ODBC de la bibliothèque Microsoft Foundation Classes (MFC) et fournit une vue d’ensemble de la façon dont les classes fonctionnent ensemble. Pour plus d’informations sur ODBC et MFC, consultez les rubriques suivantes :

- [Connexion à une source de données](connecting-to-a-data-source.md)

- [Sélection et manipulation d’enregistrements](selecting-and-manipulating-records.md)

- [Affichage et manipulation de données dans un formulaire](displaying-and-manipulating-data-in-a-form.md)

- [Utilisation des documents et des vues](working-with-documents-and-views.md)

- [Accès à ODBC et SQL](access-to-odbc-and-sql.md)

- [En savoir plus sur les classes ODBC MFC](further-reading-about-the-mfc-odbc-classes.md)

Les classes de base de données MFC basées sur ODBC sont conçues pour fournir un accès à toute base de données pour laquelle un pilote ODBC est disponible. Étant donné que les classes utilisent ODBC, votre application peut accéder aux données dans de nombreux formats de données différents et à des configurations locales/distantes différentes. Vous n’avez pas à écrire de code de cas spécial pour gérer différents systèmes de gestion de base de données (SGBD). Tant que vos utilisateurs disposent d’un pilote ODBC approprié pour les données auxquelles ils veulent accéder, ils peuvent utiliser votre programme pour manipuler les données dans les tables qui y sont stockées.

## <a name="see-also"></a>Voir aussi

[Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)
