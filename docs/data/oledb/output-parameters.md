---
title: Paramètres de sortie | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a17ff7e6e78b21267b71ba495ba10a98e29cfe7
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808848"
---
# <a name="output-parameters"></a>Paramètres de sortie

Appel d’une procédure stockée est similaire à l’exécution d’une commande SQL. La principale différence est que les procédures stockées utilisent des paramètres de sortie (ou « paramètres de sortie ») et valeurs de retour.

Dans le code suivant procédure stockée, le premier ' ? 'est la valeur de retour (phone) et le second' ?' est le paramètre d’entrée (nom) :

```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  

Vous spécifiez dans les paramètres de sortie dans le mappage de paramètre :

```  
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

Le \@_rowcount le paramètre de sortie indique le nombre de lignes ont été retourné à partir de la table de test. Toutefois, cette procédure stockée limite le nombre de lignes à 50. Par exemple, si elle existait 100 lignes dans le test, le nombre de lignes serait 50 (car ce code récupère uniquement les 50 premières lignes). S’il y avait uniquement 30 lignes dans la table, le nombre de lignes serait 30. Veillez à appeler `Close` ou `CloseAll` pour renseigner le paramètre de sortie avant d’extraire sa valeur.

## <a name="see-also"></a>Voir aussi

[Utilisation des procédures stockées](../../data/oledb/using-stored-procedures.md)