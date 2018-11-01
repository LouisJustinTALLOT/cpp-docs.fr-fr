---
title: Utilisation d'assemblys vérifiables avec SQL Server (C++/CLI)
ms.date: 10/17/2019
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
ms.openlocfilehash: 419b3de739de22597fffc7a607e2bf73561e3000
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472655"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Utilisation d'assemblys vérifiables avec SQL Server (C++/CLI)

Les procédures stockées étendues, empaquetés en tant que bibliothèques de liens dynamiques (DLL), fournissent un moyen d’étendre les fonctionnalités de SQL Server via les fonctions développées avec Visual C++. Les procédures stockées étendues sont implémentées en tant que fonctions au sein de la DLL. Outre les fonctions, procédures stockées étendues peuvent également définir [types définis par l’utilisateur](../cpp/classes-and-structs-cpp.md) et agréger des fonctions (telles que SUM ou AVG).

Lorsqu’un client exécute une procédure stockée étendue, SQL Server recherche la DLL associée à la procédure stockée étendue et charge la DLL. SQL Server appelle la procédure stockée étendue demandée et s’exécute sous un contexte de sécurité spécifié. La procédure stockée étendue, résultat de passes définit et retourne les paramètres sur le serveur.

SQL Server fournit des extensions à Transact-SQL (T-SQL) pour vous permettre d’installer des assemblys vérifiables dans SQL Server. Le jeu d’autorisations SQL Server spécifie le contexte de sécurité, avec les niveaux de sécurité suivants :

- Mode non restreint : exécuter du code à vos risques et périls ; code ne devra pas être de type sécurisé.

- Mode sans échec : exécuter sécurisé vérifié le code de type sécurisé ; compilé avec/clr : safe.

> [!IMPORTANT]
> Déconseillé de Visual Studio 2015 et Visual Studio 2017 ne prend pas en charge la **/CLR : pure** et **/CLR : safe** la création de projets vérifiables. Si vous avez besoin du code vérifiable, nous vous recommandons de que vous traduisez votre code en c#.

Pour créer et charger un assembly vérifiable dans SQL Server, utilisez les commandes Transact-SQL CREATE ASSEMBLY et DROP ASSEMBLY comme suit :

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```

La commande PERMISSION_SET spécifie le contexte de sécurité et peut avoir les valeurs UNRESTRICTED, SAFE ou étendu.

En outre, vous pouvez utiliser la commande CREATE FUNCTION pour lier aux noms de méthode dans une classe :

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```

## <a name="example"></a>Exemple

Le script SQL suivant (par exemple, « MyScript.sql nommé ») charge un assembly dans SQL Server et rend une méthode d’une classe disponible :

```sql
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

Les scripts SQL peuvent être exécutés de manière interactive dans l’Analyseur de requêtes SQL ou à la ligne de commande avec l’utilitaire sqlcmd.exe. La ligne de commande suivante se connecte à MyServer, utilise la base de données par défaut, utilise une connexion approuvée, entre MyScript.sql et renvoie MyResult.txt.

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```

## <a name="see-also"></a>Voir aussi

[Classes et structs](../cpp/classes-and-structs-cpp.md)