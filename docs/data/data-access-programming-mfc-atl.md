---
description: 'En savoir plus sur : programmation de l’accès aux données (MFC/ATL)'
title: Programmation de l’accès aux données (MFC-ATL)
ms.date: 11/16/2018
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
ms.openlocfilehash: 7785eb65bd26c6c8bf4b60d5a8a919097627f20c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136472"
---
# <a name="data-access-programming-mfcatl"></a>Programmation de l'accès aux données (MFC/ATL)

Au fil des années, Visual C++ a permis de travailler de différentes façons avec les bases de données. Dans 2011, Microsoft a annoncé qu’il s’agissait d’un alignement sur Open Database Connectivity (ODBC) comme technologie préférée pour l’accès aux produits SQL Server à partir du code natif. ODBC est un standard industriel. En l’utilisant, vous obtenez une portabilité maximale de votre code sur différentes plateformes et sources de données. La majorité des produits de base de données SQL ainsi que de nombreux produits NoSQL prennent en charge ODBC. Vous pouvez utiliser ODBC directement en appelant les API ODBC de bas niveau, ou utiliser les classes wrapper ODBC MFC et même une bibliothèque de wrappers C++ tierce.

OLE DB est une API de bas niveau ultra performante, qui repose sur la spécification COM et est uniquement prise en charge sur Windows. Utilisez OLE DB si votre programme accède à [des serveurs liés](/sql/relational-databases/linked-servers/linked-servers-database-engine). ATL fournit les modèles OLE DB qui facilitent la création des consommateurs et des fournisseurs OLE DB personnalisés. Vous trouverez le fournisseur le plus récent pour Microsoft SQL Server dans la documentation du [pilote OLE DB pour SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server).

## <a name="porting-data-applications"></a>Portage d’applications de données

Si votre application héritée utilise OLE DB ou l’interface ADO de niveau supérieur pour se connecter à SQL Server, vous devez envisager de migrer vers le dernier [pilote OLE DB pour SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server) afin de tirer parti des dernières fonctionnalités de SQL Server. Une autre solution, si vous n’avez pas besoin de la portabilité multiplateforme ou des fonctionnalités SQL Server les plus récentes, vous pouvez utiliser le fournisseur Microsoft OLE DB pour ODBC (MSDASQL).  MSDASQL permet aux applications qui reposent sur OLE DB et ADO (qui utilise OLEDB en interne) d’accéder aux sources de données via un pilote ODBC. Comme avec n’importe quelle couche de traduction, MSDASQL peut avoir une incidence sur les performances de la base de données. Vous devez procéder à des tests qui vous permettent de déterminer si l’impact est significatif pour votre application. MSDASQL est fourni avec le système d’exploitation Windows, sachant que Windows Server 2008 et Windows Vista SP1 sont les premières versions de Windows à inclure une version 64 bits de cette technologie.

Si votre application C++ se connecte à SQL Server ou Azure SQL Database via ODBC, elle doit utiliser [le pilote ODBC le plus récent](/sql/connect/odbc/download-odbc-driver-for-sql-server).

Si vous utilisez C++/CLI, vous pouvez continuer à utiliser ADO.NET, comme toujours. Pour plus d’informations, consultez [Accès aux données à l’aide d’ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) et [Accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).

- En plus des classes wrapper ODBC, MFC fournit également des classes wrapper DAO (Data Access Objects) pour la connexion aux bases de données Access.  Par contre, l’interface DAO est obsolète. Tout code basé sur CDaoDatabase ou CDaoRecordset doit être mis à niveau.

Pour plus d’informations sur l’historique des technologies d’accès aux données sur Microsoft Windows, consultez [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).

## <a name="see-also"></a>Voir aussi

[Accès aux données](data-access-in-cpp.md)<br/>
[Microsoft ODBC (Open Database Connectivity)](/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
