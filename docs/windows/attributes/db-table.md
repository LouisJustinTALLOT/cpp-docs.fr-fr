---
title: db_table (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 03d6512933d114cf1c3b06fa3fdc9eaa03c70934
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790937"
---
# <a name="dbtable"></a>db_table

Ouvre une table OLE DB.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

#### <a name="parameters"></a>Paramètres

*db_table*<br/>
Chaîne spécifiant le nom d’une table de base de données (par exemple, « produits »).

*name*<br/>
(Facultatif) Le nom de la poignée que vous utilisez pour travailler avec la table. Vous devez spécifier ce paramètre si vous souhaitez retourner plusieurs lignes de résultats. **db_table** génère une variable avec la valeur *nom* qui peut être utilisé pour parcourir l’ensemble de lignes ou d’exécuter plusieurs requêtes d’action.

*source_name*<br/>
(Facultatif) Le `CSession` variable ou une instance d’une classe qui a le `db_source` attribut appliqué à ce dernier sur lequel la commande s’exécute. Consultez [db_source](db-source.md).

*HRESULT*<br/>
(Facultatif) Identifie la variable qui recevra la valeur HRESULT de cette commande de base de données. Si la variable n’existe pas, elle est injectée automatiquement par l’attribut.

## <a name="remarks"></a>Notes

**db_table** crée un [CTable](../../data/oledb/ctable-class.md) objet, qui est utilisé par un consommateur OLE DB pour ouvrir une table. Vous pouvez utiliser cet attribut uniquement au niveau de la classe ; Vous ne pouvez pas l’utiliser en ligne. Utilisez `db_column` pour lier les colonnes de table à des variables ; utiliser `db_param` pour délimiter (définie le type de paramètre et donc sur) des paramètres.

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

Pour obtenir un exemple de cet attribut utilisé dans une application, consultez les exemples [AtlAgent](https://github.com/Microsoft/VCSamples) et [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](ole-db-consumer-attributes.md)  
