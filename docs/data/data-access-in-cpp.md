---
title: Accès aux données dans Visual C++ | Documents Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bb74d27af485f765e1330bc83ab196e1d9ba6b5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090650"
---
# <a name="data-access-in-visual-c"></a>Accès aux données dans Visual C++

Pratiquement tous les produits de base de données, SQL et NoSQL, fournissent une interface pour les applications C++ natives. L’interface standard du secteur est ODBC, qui est prise en charge par tous les principaux produits de base de données SQL et de nombreux produits NoSQL. Pour les produits non-Microsoft, contactez le fournisseur pour plus d’informations. Des bibliothèques tierces avec différents contrats de licence sont également disponibles.

Depuis 2011, Microsoft s’est aligné sur ODBC en tant que standard pour les applications natives se connectant aux bases de données Microsoft SQL Server, localement et dans le cloud. Pour plus d’informations, consultez [Programmation de l’accès aux données \(MFC-ATL\)](data-access-programming-mfc-atl.md). Les bibliothèques C++/CLI peuvent utiliser les pilotes ODBC natifs ou ADO.NET. Pour plus d’informations, consultez [Accès aux données à l’aide d’ADO.NET (C++/CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) et [Accès aux données dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>Dans cette section
[Programmation d’accès aux données (MFC/ATL)](data-access-programming-mfc-atl.md) décrit les données héritées accéder à la programmation avec Visual C++, où la meilleure façon consiste à utiliser une des bibliothèques de classes telles que la classe bibliothèque ATL (Active Template) ou la bibliothèque de Microsoft Foundation classes (MFC), qui simplifient l’utilisation des API de la base de données.

[Ouvrez la connectivité de base de données (ODBC)](odbc/open-database-connectivity-odbc.md) bibliothèque de la Microsoft Foundation Classes (MFC) fournit des classes pour la programmation avec ODBC Open Database Connectivity ().

[Programmation OLE DB](oledb/ole-db-programming.md) une interface principalement héritée qui est encore nécessaire dans certains scénarios, en particulier lorsque vous programmez par rapport à des serveurs liés.

## <a name="related-topics"></a>Rubriques connexes
[Se connecter à la base de données SQL à l’aide de C et C++](/azure/sql-database/sql-database-develop-cplusplus-simple) se connecter à la base de données SQL Azure à partir d’applications C ou C++.

[Bibliothèque cliente Microsoft Azure Storage pour C++](https://github.com/Azure/azure-storage-cpp)
[Azure Storage](/azure/storage/storage-introduction) est une solution de stockage cloud pour les applications modernes qui s’appuient sur la durabilité, la disponibilité et l’évolutivité en fonction des besoins de leur clients. Connectez-vous au service Stockage Azure à partir de C++ à l’aide de la bibliothèque cliente de stockage Azure pour C++.

[ODBC Driver 13.1 for SQL Server - Windows publié](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server) le dernier pilote ODBC fournit l’accès aux données fiable pour Microsoft SQL Server 2016 Microsoft Azure SQL Database pour les applications C/C++. Fournit la prise en charge des fonctionnalités dont est toujours chiffré, Azure Active Directory et les groupes de disponibilité AlwaysOn. Également disponible pour Mac OS et Linux.     
 
[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming) SQL Server Native Client est une données autonome accès API (API), utilisée pour OLE DB et ODBC, qui prend en charge de SQL Server 2005, SQL Server 2014. Les nouvelles applications doivent utiliser le pilote ODBC 13.1 pour SQL Server.

[Microsoft Azure C et le centre de développement C++](https://azure.microsoft.com/develop/cpp/) Azure vous permet de générer des applications C++ avec une plus grande souplesse, l’évolutivité et la fiabilité à l’aide des outils que vous aimez.    

[Comment utiliser le stockage d’objets Blob à partir de C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs) stockage d’objets Blob Azure est un service qui stocke des données non structurées dans le cloud en tant qu’objets/BLOB. Le stockage Blob permet de stocker n’importe quel type de données texte ou binaires, par exemple un document, un fichier multimédia ou un programme d’installation d’application. Le stockage Blob est également appelé stockage d’objets.

[ Référence du programmeur ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference) interface le ODBC est conçu pour une utilisation avec le langage de programmation C. L’utilisation de l’interface ODBC s’étend sur trois domaines : les instructions SQL, les appels de fonctions ODBC et la programmation en C.

## <a name="see-also"></a>Voir aussi
[Visual C++](../visual-cpp-in-visual-studio.md)
