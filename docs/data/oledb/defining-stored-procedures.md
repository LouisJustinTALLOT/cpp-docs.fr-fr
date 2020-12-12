---
description: 'En savoir plus sur : définition des procédures stockées'
title: Définition de procédures stockées
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 52527da031093d82c9d74be5807a5de26f3ee091
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317686"
---
# <a name="defining-stored-procedures"></a>Définition de procédures stockées

Avant d’appeler une procédure stockée, vous devez d’abord la définir à l’aide de la macro [DEFINE_COMMAND](./macros-and-global-functions-for-ole-db-consumer-templates.md#define_command) . Lorsque vous définissez la commande, indiquez les paramètres avec un point d’interrogation ( ?) comme marqueur de paramètre :

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

La syntaxe (l’utilisation d’accolades, etc.) utilisée dans les exemples de code de cette rubrique est spécifique à SQL Server. La syntaxe que vous utilisez dans vos procédures stockées peut varier selon le fournisseur que vous utilisez.

Ensuite, dans le mappage de paramètres, spécifiez les paramètres que vous avez utilisés dans la commande, en répertoriant les paramètres dans l’ordre dans lequel ils se produisent dans la commande :

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

L’exemple précédent définit une procédure stockée au fur et à mesure. En général, pour une réutilisation efficace du code, une base de données contient un ensemble de procédures stockées prédéfinies avec des noms tels que `Sales by Year` ou `dt_adduserobject` . Vous pouvez afficher leurs définitions à l’aide du gestionnaire de SQL Server Entreprise. Vous les appelez comme suit (le positionnement de l’opérateur *?* les paramètres dépendent de l’interface de la procédure stockée) :

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

Ensuite, déclarez la classe de commande :

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

Enfin, appelez la procédure stockée dans `OpenRowset` comme suit :

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

Notez également que vous pouvez définir une procédure stockée à l’aide de l’attribut de base de données [db_command](../../windows/attributes/db-command.md) comme suit :

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>Voir aussi

[Utilisation de procédures stockées](../../data/oledb/using-stored-procedures.md)
