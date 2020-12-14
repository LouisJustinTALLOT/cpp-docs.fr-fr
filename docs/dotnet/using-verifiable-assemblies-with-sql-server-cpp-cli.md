---
description: 'En savoir plus sur : utilisation d’assemblys vérifiables avec SQL Server (C++/CLI)'
title: Utilisation d'assemblys vérifiables avec SQL Server (C++/CLI)
ms.date: 10/17/2018
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
ms.openlocfilehash: b155fb0360fb373f5931f51de3af557d06858a71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204197"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Utilisation d'assemblys vérifiables avec SQL Server (C++/CLI)

Les procédures stockées étendues, empaquetées en tant que bibliothèques de liens dynamiques (dll), permettent d’étendre les fonctionnalités de SQL Server par le biais de fonctions développées avec Visual C++. Les procédures stockées étendues sont implémentées en tant que fonctions dans des dll. Outre les fonctions, les procédures stockées étendues peuvent également définir des [types définis par l’utilisateur](../cpp/classes-and-structs-cpp.md) et des fonctions d’agrégation (telles que SUM ou AVG).

Lorsqu’un client exécute une procédure stockée étendue, SQL Server recherche la DLL associée à la procédure stockée étendue et charge la DLL. SQL Server appelle la procédure stockée étendue demandée et l’exécute dans un contexte de sécurité spécifié. La procédure stockée étendue transmet ensuite les jeux de résultats et retourne les paramètres au serveur.

SQL Server fournit des extensions à Transact-SQL (T-SQL) pour vous permettre d’installer des assemblys vérifiables dans SQL Server. Le jeu d’autorisations SQL Server spécifie le contexte de sécurité, avec les niveaux de sécurité suivants :

- Mode non restreint : exécuter le code à vos propres risques ; Il n’est pas nécessaire que le code soit de type sécurisé vérifié.

- Mode sans échec : exécutez le code de sécurité sécurisée. compilé avec/clr : safe.

> [!IMPORTANT]
> Visual Studio 2015 déconseillé et Visual Studio 2017 ne prend pas en charge la création de projets vérifiables **/clr : pure** et **/clr : safe** . Si vous avez besoin de code vérifiable, nous vous recommandons de traduire votre code en C#.

Pour créer et charger un assembly vérifiable dans SQL Server, utilisez les commandes Transact-SQL CREATe ASSEMBLy et DROP ASSEMBLy comme suit :

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```

La commande PERMISSION_SET spécifie le contexte de sécurité et peut avoir les valeurs Unlimited, SAFE ou EXTENDED.

En outre, vous pouvez utiliser la commande CREATe FUNCTION pour créer une liaison avec les noms de méthode dans une classe :

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```

## <a name="example"></a>Exemple

Le script SQL suivant (par exemple, nommé « Monscript. Sql ») charge un assembly dans SQL Server et rend une méthode d’une classe disponible :

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

Les scripts SQL peuvent être exécutés de manière interactive dans l’analyseur de requêtes SQL ou à partir de la ligne de commande avec l’utilitaire sqlcmd.exe. La ligne de commande suivante se connecte à MyServer, utilise la base de données par défaut, utilise une connexion approuvée, les entrées Monscript. SQL et les sorties MyResult.txt.

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```

## <a name="see-also"></a>Voir aussi

[Classes et structs](../cpp/classes-and-structs-cpp.md)
