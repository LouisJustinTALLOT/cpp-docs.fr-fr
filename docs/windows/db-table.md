---
title: db_table | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_table
dev_langs:
- C++
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81379a6da96b084239a083bc930cf8e792d518a2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649749"
---
# <a name="dbtable"></a>db_table
Ouvre une table OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *db_table*  
 Chaîne spécifiant le nom d’une table de base de données (par exemple, « produits »).  
  
 *name* (facultatif)  
 Le nom de la poignée que vous utilisez pour travailler avec la table. Vous devez spécifier ce paramètre si vous souhaitez retourner plusieurs lignes de résultats. **db_table** génère une variable avec la valeur *nom* qui peut être utilisé pour parcourir l’ensemble de lignes ou d’exécuter plusieurs requêtes d’action.  
  
 *source_name* (facultatif)  
 Variable `CSession` ou instance d’une classe à laquelle l’attribut `db_source` est appliqué et sur laquelle la commande est exécutée. Voir [db_source](../windows/db-source.md).  
  
 *HRESULT* (facultatif)  
 Identifie la variable qui recevra la valeur HRESULT de cette commande de base de données. Si la variable n’existe pas, elle est injectée automatiquement par l’attribut.  
  
## <a name="remarks"></a>Notes  
 **db_table** crée un [CTable](../data/oledb/ctable-class.md) objet, qui est utilisé par un consommateur OLE DB pour ouvrir une table. Vous pouvez utiliser cet attribut uniquement au niveau de la classe ; Vous ne pouvez pas l’utiliser en ligne. Utilisez `db_column` pour lier les colonnes de table à des variables ; utiliser `db_param` pour délimiter (définie le type de paramètre et donc sur) des paramètres.  
  
 Lorsque le fournisseur d’attributs consommateur applique cet attribut à une classe, le compilateur renomme la classe à \_ *Nom_de_votre_classe*accesseur, où *Nom_de_votre_classe* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *Nom_de_votre_classe*, qui dérive à son \_ *Nom_de_votre_classe*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant ouvre le tableau de produits pour une utilisation par `CProducts`.  
  
```cpp  
// db_table.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_table(L"dbo.Products") ]  
class CProducts {  
   [ db_column("1") ] LONG m_ProductID;  
};  
```  
  
 Pour obtenir un exemple de cet attribut utilisé dans une application, consultez les exemples [AtlAgent](http://msdn.microsoft.com/52bef5da-c1a0-4223-b4e6-9e464b6db409) et [MultiRead](http://msdn.microsoft.com/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **struct**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md)   