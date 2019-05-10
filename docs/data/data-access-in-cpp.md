---
title: Accès aux données dans Visual C++
ms.date: 03/28/2017
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
ms.openlocfilehash: a68c4a9df3b439ae641c5e4cbe6f3fbc8b8e6355
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222534"
---
# <a name="data-access-in-visual-c"></a>Accès aux données dans Visual C++

Pratiquement tous les produits de base de données, SQL et NoSQL, fournissent une interface pour les applications C++ natives. L’interface standard du secteur est ODBC, qui est prise en charge par tous les principaux produits de base de données SQL et de nombreux produits NoSQL. Pour les produits non-Microsoft, contactez le fournisseur pour plus d’informations. Des bibliothèques tierces avec différents contrats de licence sont également disponibles.

Depuis 2011, Microsoft s’est aligné sur ODBC en tant que standard pour les applications natives se connectant aux bases de données Microsoft SQL Server, localement et dans le cloud. Pour plus d’informations, consultez [Programmation de l’accès aux données \(MFC-ATL\)](data-access-programming-mfc-atl.md). Les bibliothèques C++/CLI peuvent utiliser les pilotes ODBC natifs ou ADO.NET. Pour plus d’informations, consultez [Accès aux données à l’aide d’ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) et [Accès aux données dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>Dans cette section

[Accès aux données de programmation (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
Décrit la programmation de l'accès aux données héritées avec Visual C++, où la meilleure méthode consiste à utiliser l'une des bibliothèques de classes telles que la bibliothèque ATL (Active Template Library) ou la bibliothèque MFC (Microsoft Foundation Class), qui simplifient l'utilisation des API de base de données.

[ODBC (Open Database Connectivity)](odbc/open-database-connectivity-odbc.md)<br/>
La bibliothèque Microsoft Foundation Classes (MFC) fournit des classes pour la programmation avec Open Database Connectivity (ODBC).

[Programmation OLE DB](oledb/ole-db-programming.md)<br/>
Interface principalement héritée qui est toujours requis dans certains scénarios, en particulier lorsque vous programmez sur des serveurs liés.

## <a name="related-topics"></a>Rubriques connexes

[Se connecter à la base de données SQL à l’aide de C et C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Connectez-vous à la base de données SQL Azure à partir d’applications C ou C++.

[Bibliothèque cliente de stockage Microsoft Azure pour C++](https://github.com/Azure/azure-storage-cpp)<br/>
Le service [Stockage Azure](/azure/storage/storage-introduction) est une solution de stockage cloud pour les applications modernes qui s’appuient sur la durabilité, la disponibilité et la scalabilité afin de répondre aux besoins de leurs clients. Connectez-vous au service Stockage Azure à partir de C++ à l’aide de la bibliothèque cliente de stockage Azure pour C++.

[Pilote ODBC pour SQL Server](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
Le dernier pilote ODBC fournit l’accès aux données robuste pour Microsoft SQL Server et Microsoft Azure SQL Database pour C /C++ en fonction des applications. Fournit la prise en charge des fonctionnalités, notamment est toujours chiffré, Azure Active Directory et les groupes de disponibilité AlwaysOn. Également disponible pour Mac OS et Linux.

[OLE DB Driver pour SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
Le dernier pilote OLE DB est une données autonome accès application interface de programmation (API) qui prend en charge de Microsoft SQL Server et Microsoft Azure SQL Database.

[Microsoft Azure C et C++ Developer Center](https://azure.microsoft.com/develop/cpp/)<br/>
Azure facilite la création d’applications C++ avec plus de souplesse, de scalabilité et de fiabilité à l’aide des outils que vous aimez.

[Comment utiliser le stockage d’objets Blob à partir de C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Le stockage Blob Azure est un service qui stocke les données non structurées dans le cloud en tant qu’objets/objets blob. Le stockage Blob permet de stocker n’importe quel type de données texte ou binaires, par exemple un document, un fichier multimédia ou un programme d’installation d’application. Le stockage Blob est également appelé stockage d’objets.

[ Référence du programmeur ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
L’interface ODBC est conçue pour une utilisation avec le langage de programmation C. Utilisation de l’interface ODBC s’étend sur trois domaines : Instructions SQL, appels de fonction ODBC et programmation en C.

## <a name="see-also"></a>Voir aussi

[Visual C++](../overview/visual-cpp-in-visual-studio.md)
