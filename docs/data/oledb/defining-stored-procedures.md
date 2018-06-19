---
title: Définition de procédures stockées | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 1e03a5ae2e7c75d905216a6be92630376484d047
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101300"
---
# <a name="defining-stored-procedures"></a>Définition des procédures stockées
Avant d’appeler une procédure stockée, vous devez tout d’abord définir, en utilisant le [DEFINE_COMMAND](../../data/oledb/define-command.md) (macro). Lorsque vous définissez la commande, désignez les paramètres avec un point d’interrogation ( ?) comme marqueur de paramètre :  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 Notez que la syntaxe (l’utilisation d’accolades, etc.) utilisée dans les exemples de code dans cette rubrique est spécifique à SQL Server. La syntaxe que vous utilisez dans vos procédures stockées peut varier selon le fournisseur que vous utilisez.  
  
 Ensuite, dans le mappage de paramètre, spécifiez les paramètres que vous avez utilisé dans la commande, qui répertorie les paramètres dans l’ordre où ils apparaissent dans la commande :  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 L’exemple précédent définit une procédure stockée lorsqu’il passe. En règle générale, pour une réutilisation efficace du code, une base de données contient un ensemble de procédures stockées prédéfinies portant des noms comme « Ventes par année » ou « dt_adduserobject ». Vous pouvez afficher ces définitions à l’aide de SQL Server Enterprise Manager. Vous les appelez comme suit (le placement de la « ? » dépend des paramètres sur l’interface de la procédure stockée) :  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 Ensuite, déclarez la classe de commande :  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
 Enfin, appelez la procédure stockée dans `OpenRowset` comme suit :  
  
```  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
 Notez également que vous pouvez définir une procédure stockée à l’aide de l’attribut de base de données [db_command](../../windows/db-command.md) comme suit :  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des procédures stockées](../../data/oledb/using-stored-procedures.md)