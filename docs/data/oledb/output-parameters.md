---
title: Paramètres de sortie
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: 196c50ea62c3e3188b61a3b35a9e2752740c4ad5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283938"
---
# <a name="output-parameters"></a>Paramètres de sortie

Appel d’une procédure stockée est similaire à l’exécution d’une commande SQL. La principale différence est que les procédures stockées utilisent des paramètres de sortie (ou « paramètres de sortie ») et valeurs de retour.

Dans le code suivant procédure stockée, le premier ' ? 'est la valeur de retour (phone) et le second' ?' est le paramètre d’entrée (nom) :

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

Vous spécifiez dans les paramètres de sortie dans le mappage de paramètre :

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

Votre application doit gérer la sortie retournée à partir de procédures stockées. Différents fournisseurs OLE DB retournent des paramètres de sortie et retournent des valeurs à différents moments pendant le traitement des résultats. Par exemple, le fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB) ne fournit les paramètres de sortie et codes de retour qu’une fois que le consommateur a récupéré ou annulé les jeux de résultats retournés par la procédure stockée. La sortie est retournée dans le dernier paquet TDS à partir du serveur.

## <a name="row-count"></a>Nombre de lignes

Si vous utilisez les modèles du consommateur OLE DB pour exécuter une procédure stockée qui a des paramètres de sortie, le nombre de lignes n’est pas défini jusqu'à la fermeture de l’ensemble de lignes.

Par exemple, considérez une procédure stockée avec un ensemble de lignes et un paramètre de sortie :

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

Le `@_rowcount` paramètre de sortie indique le nombre de lignes ont été retourné à partir de la table de test. Toutefois, cette procédure stockée limite le nombre de lignes à 50. Par exemple, si elle existait 100 lignes dans le test, le nombre de lignes serait 50 (car ce code récupère uniquement les 50 premières lignes). S’il y avait uniquement 30 lignes dans la table, le nombre de lignes serait 30. Veillez à appeler `Close` ou `CloseAll` pour renseigner le paramètre de sortie avant d’extraire sa valeur.

## <a name="see-also"></a>Voir aussi

[Utilisation des procédures stockées](../../data/oledb/using-stored-procedures.md)