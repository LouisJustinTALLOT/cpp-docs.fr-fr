---
title: Définition de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9d5cbe04ac5ad23fef09d53e747dab8c4c4b53b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053135"
---
# <a name="defining-stored-procedures"></a>Définition des procédures stockées

Avant d’appeler une procédure stockée, vous devez tout d’abord définir, en utilisant le [DEFINE_COMMAND](../../data/oledb/define-command.md) macro. Lorsque vous définissez la commande, désigner des paramètres avec un point d’interrogation ( ?) comme marqueur de paramètre :

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

La syntaxe (l’utilisation d’accolades, etc.) utilisée dans les exemples de code dans cette rubrique est spécifique à SQL Server. La syntaxe que vous utilisez dans vos procédures stockées peut-être varier selon le fournisseur que vous utilisez.

Ensuite, dans le mappage de paramètre, spécifiez les paramètres que vous avez utilisé dans la commande, en listant les paramètres dans l’ordre où ils apparaissent dans la commande :

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

L’exemple précédent définit une procédure stockée, tandis qu’elle passe. En règle générale, pour une réutilisation efficace du code, une base de données contient un ensemble de procédures stockées prédéfinies avec des noms tels que `Sales by Year` ou `dt_adduserobject`. Vous pouvez afficher ces définitions à l’aide de SQL Server Enterprise Manager. Vous les appelez comme suit (le placement de la *?* paramètres dépendent interface de la procédure stockée) :

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

Ensuite, déclarez la classe de commande :

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

Enfin, appelez la procédure stockée `OpenRowset` comme suit :

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

Notez également que vous pouvez définir une procédure stockée à l’aide de l’attribut de base de données [db_command](../../windows/db-command.md) comme suit :

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>Voir aussi

[Utilisation des procédures stockées](../../data/oledb/using-stored-procedures.md)