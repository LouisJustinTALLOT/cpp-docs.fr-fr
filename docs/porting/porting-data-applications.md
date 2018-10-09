---
title: Portage d’applications de données | Microsoft Docs
ms.custom: ''
ms.date: 05/12/2017
ms.technology:
- devlang-cpp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 8d10c285-c13f-4e6e-a09e-5ee0f2666b44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3dcbab39bdf6a9a944b3cd6200302d89a30d163d
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820742"
---
# <a name="porting-data-applications"></a>Portage d’applications de données
Au fil des années, Visual C++ a permis de travailler de différentes façons avec les bases de données. En 2011, Microsoft a annoncé son alignement à ODBC, comme technologie recommandée pour l’accès aux produits SQL Server à partir du code natif. ODBC est un standard industriel. En l’utilisant, vous obtenez une portabilité maximale de votre code sur différentes plateformes et sources de données. La majorité des produits de base de données SQL ainsi que de nombreux produits NoSQL prennent en charge ODBC. Vous pouvez utiliser ODBC directement en appelant les API ODBC de bas niveau, ou utiliser les classes wrapper ODBC MFC et même une bibliothèque de wrappers C++ tierce. 

OLE DB est une API de bas niveau ultra performante, qui repose sur la spécification COM et est uniquement prise en charge sur Windows. Utilisez OLE DB si votre programme accède à [des serveurs liés](/sql/relational-databases/linked-servers/linked-servers-database-engine). ATL fournit les modèles OLE DB qui facilitent la création des consommateurs et des fournisseurs OLE DB personnalisés. La version la plus récente d’OLE DB fournie dans SQL Native Client 11.  

Si votre application héritée utilise OLE DB ou l’interface ADO de niveau supérieur pour se connecter à SQL Server et que vous n’accédez pas aux serveurs liés, vous devez envisager de migrer vers ODBC dans un futur proche. Si vous n’avez pas besoin de la portabilité multiplateforme ou des dernières fonctionnalités de SQL Server, vous pouvez éventuellement utiliser le fournisseur Microsoft OLE DB pour ODBC (MSDASQL).  MSDASQL permet aux applications qui reposent sur OLE DB et ADO (qui utilise OLEDB en interne) d’accéder aux sources de données via un pilote ODBC. Comme avec n’importe quelle couche de traduction, MSDASQL peut avoir une incidence sur les performances de la base de données. Vous devez procéder à des tests qui vous permettent de déterminer si l’impact est significatif pour votre application. MSDASQL est fourni avec le système d’exploitation Windows, sachant que Windows Server 2008 et Windows Vista SP1 sont les premières versions de Windows à inclure une version 64 bits de cette technologie.

Le composant SNAC (SQL Native Client), qui empaquette les pilotes OLE DB et ODBC dans une même DLL, est déprécié pour les applications ODBC. La version SQL Server 2012 de SNAC (SQLNCLI11.DLL) est fournie avec SQL Server 2016, car différents composants de SQL Server en dépendent. Toutefois, les nouvelles applications C++ qui se connectent à SQL Server ou à SQL Azure Database via ODBC doivent utiliser [le pilote ODBC le plus récent](/sql/connect/odbc/download-odbc-driver-for-sql-server). Pour plus d’informations, consultez [Programmation de SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming)

Si vous utilisez C++/CLI, vous pouvez continuer à utiliser ADO.NET, comme toujours. Pour plus d’informations, consultez [Accès aux données à l’aide d’ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) et [Accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).  
  
- En plus des classes wrapper ODBC, MFC fournit également des classes wrapper DAO (Data Access Objects) pour la connexion aux bases de données Access.  Par contre, l’interface DAO est obsolète. Tout code basé sur `CDaoDatabase` ou `CDaoRecordset` doit être mis à niveau. 

Pour plus d’informations sur l’historique des technologies d’accès aux données sur Microsoft Windows, consultez [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).  

## <a name="see-also"></a>Voir aussi  
 
[Accès aux données dans Visual C++](../data/data-access-in-cpp.md)<br/>
[Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
[Feuille de route des technologies d’accès aux données](https://msdn.microsoft.com/library/ms810810.aspx)  