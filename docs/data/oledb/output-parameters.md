---
description: 'En savoir plus sur : paramètres de sortie'
title: Paramètres de sortie
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: c52877483d40d7de1a8313eb806769ce92af7337
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316932"
---
# <a name="output-parameters"></a>Paramètres de sortie

L’appel d’une procédure stockée est similaire à l’exécution d’une commande SQL. La principale différence réside dans le fait que les procédures stockées utilisent des paramètres de sortie (ou des « paramètres de sortie ») et des valeurs de retour.

Dans la procédure stockée suivante, le premier «  ? » est la valeur de retour (Phone) et le deuxième «  ? » est le paramètre d’entrée (Name) :

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

Vous spécifiez les paramètres in et out dans le mappage de paramètres :

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

Votre application doit gérer la sortie retournée par les procédures stockées. Des fournisseurs OLE DB différents retournent des paramètres de sortie et des valeurs de retour à des moments différents pendant le traitement des résultats. Par exemple, le fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB) ne fournit pas de paramètres de sortie et de codes de retour tant que le consommateur n’a pas récupéré ou annulé les jeux de résultats retournés par la procédure stockée. La sortie est retournée dans le dernier paquet TDS à partir du serveur.

## <a name="row-count"></a>Nombre de lignes

Si vous utilisez les modèles de consommateur OLE DB pour exécuter une procédure stockée qui a des paramètres de paramètre, le nombre de lignes n’est pas défini tant que vous n’avez pas fermé l’ensemble de lignes.

Par exemple, considérez une procédure stockée avec un ensemble de lignes et un paramètre d’inversion :

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

Le `@_rowcount` paramètre unparameter signale le nombre de lignes retournées à partir de la table de test. Toutefois, cette procédure stockée limite le nombre de lignes à 50. Par exemple, s’il y a 100 lignes dans le test, le ROWCOUNT est 50 (car ce code récupère uniquement les 50 lignes supérieures). S’il n’y avait que 30 lignes dans la table, le ROWCOUNT est de 30. Veillez à appeler `Close` ou `CloseAll` à remplir le paramètre out avant de récupérer sa valeur.

## <a name="see-also"></a>Voir aussi

[Utilisation de procédures stockées](../../data/oledb/using-stored-procedures.md)
