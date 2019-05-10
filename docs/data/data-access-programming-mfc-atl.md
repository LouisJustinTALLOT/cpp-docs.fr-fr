---
title: Accès aux données de programmation (MFC-ATL)
ms.date: 11/16/2018
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
ms.openlocfilehash: e71e16bef29239e0c6a391b2d5e2129042cd52fa
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221847"
---
# <a name="data-access-programming-mfcatl"></a>Programmation de l'accès aux données (MFC/ATL)

Au fil des années, Visual C++ a permis de travailler de différentes façons avec les bases de données. En 2011 Microsoft a annoncé son alignement sur ODBC Open Database Connectivity () comme technologie recommandée pour l’accès aux produits SQL Server à partir du code natif. ODBC est un standard industriel. En l’utilisant, vous obtenez une portabilité maximale de votre code sur différentes plateformes et sources de données. La majorité des produits de base de données SQL ainsi que de nombreux produits NoSQL prennent en charge ODBC. Vous pouvez utiliser ODBC directement en appelant les API ODBC de bas niveau, ou utiliser les classes wrapper ODBC MFC et même une bibliothèque de wrappers C++ tierce.

OLE DB est une API de bas niveau ultra performante, qui repose sur la spécification COM et est uniquement prise en charge sur Windows. Utilisez OLE DB si votre programme accède à [des serveurs liés](/sql/relational-databases/linked-servers/linked-servers-database-engine). ATL fournit les modèles OLE DB qui facilitent la création des consommateurs et des fournisseurs OLE DB personnalisés. Vous trouverez le fournisseur le plus récent pour Microsoft SQL Server dans la documentation relative à la [OLE DB Driver pour SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server).

## <a name="porting-data-applications"></a>Portage d’applications de données

Si votre application héritée utilise OLE DB ou l’interface ADO de niveau supérieur pour se connecter à SQL Server, vous devez envisager de migrer vers la dernière version [OLE DB Driver pour SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server) pour tirer parti des dernières fonctionnalités de SQL Server. Une autre alternative, si vous n’avez pas besoin d’une portabilité multiplateforme ou les dernières fonctionnalités de SQL Server, vous pouvez éventuellement utiliser le fournisseur Microsoft OLE DB pour ODBC (MSDASQL).  MSDASQL permet aux applications qui reposent sur OLE DB et ADO (qui utilise OLEDB en interne) d’accéder aux sources de données via un pilote ODBC. Comme avec n’importe quelle couche de traduction, MSDASQL peut avoir une incidence sur les performances de la base de données. Vous devez procéder à des tests qui vous permettent de déterminer si l’impact est significatif pour votre application. MSDASQL est fourni avec le système d’exploitation Windows, sachant que Windows Server 2008 et Windows Vista SP1 sont les premières versions de Windows à inclure une version 64 bits de cette technologie.

Si votre C++ application se connecte à SQL Server ou Azure SQL Database via ODBC, elle doit utiliser [le dernier pilote ODBC](/sql/connect/odbc/download-odbc-driver-for-sql-server).

Si vous utilisez C++/CLI, vous pouvez continuer à utiliser ADO.NET, comme toujours. Pour plus d’informations, consultez [Accès aux données à l’aide d’ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) et [Accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).

- En plus des classes wrapper ODBC, MFC fournit également des classes wrapper DAO (Data Access Objects) pour la connexion aux bases de données Access.  Par contre, l’interface DAO est obsolète. Tout code basé sur CDaoDatabase ou CDaoRecordset doit être mis à niveau.

Pour plus d’informations sur l’historique des technologies d’accès aux données sur Microsoft Windows, consultez [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).

## <a name="see-also"></a>Voir aussi

[Accès aux données](data-access-in-cpp.md)<br/>
[Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
