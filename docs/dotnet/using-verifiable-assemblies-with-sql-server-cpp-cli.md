---
title: Utilisation d’assemblys vérifiables avec SQL Server (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f172eea3108771e129636e9aa95d721d45c99609
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168644"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Utilisation d'assemblys vérifiables avec SQL Server (C++/CLI)
Procédures stockées étendues, empaquetées comme bibliothèques de liens dynamiques (DLL), permettent d’étendre les fonctionnalités de SQL Server via les fonctions développées à l’aide de Visual C++. Les procédures stockées étendues sont implémentées en tant que fonctions dans les DLL. En plus des fonctions, procédures stockées étendues peuvent également définir [types définis par l’utilisateur](../cpp/classes-and-structs-cpp.md) et [des fonctions d’agrégation](http://msdn.microsoft.com/en-us/de255454-f45e-4281-81f9-bc61893ac5da) (telles que SUM ou AVG).  
  
 Lorsqu’un client exécute une procédure stockée étendue, SQL Server recherche la DLL associée à la procédure stockée étendue et charge la DLL. SQL Server appelle la procédure stockée étendue demandée et l’exécute sous un contexte de sécurité spécifié. La procédure stockée étendue transmet résultat définit et retourne les paramètres sur le serveur.  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)] Fournit des extensions à Transact-SQL (T-SQL) pour vous permettre d’installer des assemblys vérifiables dans SQL Server. Le jeu d’autorisations SQL Server spécifie le contexte de sécurité, avec les niveaux de sécurité suivants :  
  
-   Mode non restreint : exécuter du code à vos propres risques ; code n’a pas besoin être de type sécurisé.  
  
-   Mode sans échec : exécuter sécurisé vérifié le code de type sécurisé ; compilé avec/clr : safe.  
  
 Mode sans échec nécessite les assemblys exécutés être vérifiable de type sécurisé.  
  
 Pour créer et charger un assembly vérifiable dans SQL Server, utilisez les commandes Transact-SQL CREATE ASSEMBLY et déplacement ASSEMBLY comme suit :  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 La commande PERMISSION_SET spécifie le contexte de sécurité et peut avoir les valeurs UNRESTRICTED, SAFE ou EXTENDED.  
  
 En outre, vous pouvez utiliser la commande CREATE FUNCTION pour lier à des noms de méthode dans une classe :  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## <a name="example"></a>Exemple  
 Le script SQL suivant (par exemple, « MyScript.sql nommé ») charge un assembly dans SQL Server et rend une méthode d’une classe disponible :  
  
```  
-- Create assembly without external access  
drop assembly stockNoEA  
go  
create assembly stockNoEA  
from   
'c:\stockNoEA.dll'  
with permission_set safe  
  
-- Create function on assembly with no external access  
drop function GetQuoteNoEA  
go  
create function GetQuoteNoEA(@sym nvarchar(10))  
returns real  
external name stockNoEA:StockQuotes::GetQuote  
go  
  
-- To call the function  
select dbo.GetQuoteNoEA('MSFT')  
go  
```  
  
 Scripts SQL peuvent être exécutées de manière interactive dans l’Analyseur de requêtes SQL ou à la ligne de commande avec l’utilitaire sqlcmd.exe. La ligne de commande se connecte à MyServer, utilise la base de données par défaut, utilise une connexion approuvée, entre MyScript.sql et renvoie MyResult.txt.  
  
```  
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : migrer vers/clr : safe (C + c++ / CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [Classes et structs](../cpp/classes-and-structs-cpp.md)