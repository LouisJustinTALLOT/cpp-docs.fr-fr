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
ms.openlocfilehash: a1645c1116daa66c578a6d6e697ab168e4006af9
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150951"
---
# <a name="data-access-in-visual-c"></a>Accès aux données dans Visual C++

Pratiquement tous les produits de base de données, SQL et NoSQL, fournissent une interface pour les applications C++ natives. L’interface standard du secteur est ODBC, qui est prise en charge par tous les principaux produits de base de données SQL et de nombreux produits NoSQL. Pour les produits non-Microsoft, contactez le fournisseur pour plus d’informations. Des bibliothèques tierces avec différents contrats de licence sont également disponibles.

Depuis 2011, Microsoft s’est aligné sur ODBC en tant que standard pour les applications natives se connectant aux bases de données Microsoft SQL Server, localement et dans le cloud. Pour plus d’informations, consultez [Programmation de l’accès aux données \(MFC-ATL\)](data-access-programming-mfc-atl.md). Les bibliothèques C++/CLI peuvent utiliser les pilotes ODBC natifs ou ADO.NET. Pour plus d’informations, consultez [Accès aux données à l’aide d’ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) et [Accès aux données dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>Dans cette section

[Programmation de l’accès aux données (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
Décrit la programmation de l'accès aux données héritées avec Visual C++, où la meilleure méthode consiste à utiliser l'une des bibliothèques de classes telles que la bibliothèque ATL (Active Template Library) ou la bibliothèque MFC (Microsoft Foundation Class), qui simplifient l'utilisation des API de base de données.

[ODBC (Open Database Connectivity)](odbc/open-database-connectivity-odbc.md)<br/>
La bibliothèque Microsoft Foundation Classes (MFC) fournit des classes pour la programmation avec Open Database Connectivity (ODBC).

[Programmation OLE DB](oledb/ole-db-programming.md)<br/>
Interface principalement héritée qui est toujours nécessaire dans certains scénarios, en particulier quand vous programmez pour des serveurs liés.

## <a name="related-topics"></a>Rubriques connexes

[Se connecter à SQL Database avec C et C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Connectez-vous à Azure SQL Database à partir d’applications C ou C++.

[Microsoft Azure Storage Client Library for C++](https://github.com/Azure/azure-storage-cpp)<br/>
Le service [Stockage Azure](/azure/storage/storage-introduction) est une solution de stockage cloud pour les applications modernes qui s’appuient sur la durabilité, la disponibilité et la scalabilité afin de répondre aux besoins de leurs clients. Connectez-vous au service Stockage Azure à partir de C++ à l’aide de la bibliothèque cliente de stockage Azure pour C++.

[Pilote ODBC pour SQL Server](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
Le dernier pilote ODBC fournit un accès robuste aux données de Microsoft SQL Server et Microsoft Azure SQL Database pour les applications C/C++. Fournit la prise en charge des fonctionnalités comme Always Encrypted, Azure Active Directory et les groupes de disponibilité AlwaysOn. Également disponible pour Mac OS et Linux.

[OLE DB Driver pour SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
Le dernier pilote OLE DB est une API d’accès aux données autonome qui prend en charge Microsoft SQL Server et Microsoft Azure SQL Database.

[Centre de développement Microsoft Azure C et C++](https://azure.microsoft.com/develop/cpp/)<br/>
Azure facilite la création d’applications C++ avec plus de souplesse, de scalabilité et de fiabilité à l’aide des outils que vous aimez.

[Utilisation du stockage d'objets blob à partir de C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Le stockage d’objets blob Azure est un service qui stocke des données non structurées dans le cloud en tant qu’objets/blobs. Ce service peut stocker tout type de données texte ou binaires, par exemple, un document, un fichier multimédia ou un programme d’installation d’application. Le stockage d’objets blob est également appelé Stockage Blob.

[Guide de référence du programmeur ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
L’interface ODBC est conçue pour une utilisation avec le langage de programmation C. L’utilisation de l’interface ODBC s’étend sur trois domaines : les instructions SQL, les appels de fonctions ODBC et la programmation en C.

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)
