---
description: 'En savoir plus sur : db_table'
title: db_table (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 3d871961a8ded6070127e5e562615018a4320162
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333048"
---
# <a name="db_table"></a>db_table

Ouvre une table OLE DB.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

### <a name="parameters"></a>Paramètres

*db_table*<br/>
Chaîne spécifiant le nom d’une table de base de données (par exemple, « Products »).

*name*<br/>
Facultatif Nom du handle que vous utilisez pour travailler avec la table. Vous devez spécifier ce paramètre si vous souhaitez retourner plusieurs lignes de résultats. **db_table** génère une variable avec le *nom* spécifié qui peut être utilisée pour parcourir l’ensemble de lignes ou pour exécuter plusieurs requêtes d’action.

*source_name*<br/>
Facultatif `CSession` Variable ou instance d’une classe à laquelle l' `db_source` attribut est appliqué et sur lequel la commande s’exécute. Voir [db_source](db-source.md).

*signé*<br/>
Facultatif Identifie la variable qui recevra le HRESULT de cette commande de base de données. Si la variable n’existe pas, elle est injectée automatiquement par l’attribut.

## <a name="remarks"></a>Notes

**db_table** crée un objet [CTable](../../data/oledb/ctable-class.md) , qui est utilisé par un consommateur OLE DB pour ouvrir une table. Vous pouvez utiliser cet attribut uniquement au niveau de la classe ; vous ne pouvez pas l’utiliser en ligne. Utilisez `db_column` pour lier des colonnes de table à des variables ; utilisez `db_param` pour délimiter (définir le type de paramètre, etc.) des paramètres.

Lorsque le fournisseur d’attributs du consommateur applique cet attribut à une classe, le compilateur renomme la classe en \_ accesseur *YourClassName*, où *YourClassName* est le nom que vous avez donné à la classe, et le compilateur crée également une classe appelée *YourClassName*, qui dérive de l' \_ accesseur *YourClassName*.  Dans l’affichage de classes, vous verrez les deux classes.

## <a name="example"></a>Exemple

L’exemple suivant ouvre la table Products pour une utilisation par `CProducts` .

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

Pour obtenir un exemple de cet attribut utilisé dans une application, consultez [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](ole-db-consumer-attributes.md)
