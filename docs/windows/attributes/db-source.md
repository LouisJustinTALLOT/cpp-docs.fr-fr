---
title: db_source (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11a58511684a58ebb0b8ec13138bfbdb7afa4729
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081901"
---
# <a name="dbsource"></a>db_source

Crée une connexion à une source de données.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>Paramètres

*db_source*<br/>
Chaîne de connexion utilisée pour se connecter à la source de données. Pour le format de la chaîne de connexion, consultez [chaînes de connexion et des liaisons de données](/previous-versions/windows/desktop/ms718376) dans le Kit de développement logiciel Microsoft Data Access Components (MDAC).

*name*<br/>
(Facultatif) Lorsque vous utilisez **db_source** sur une classe, *nom* est une instance d’un objet de source de données qui a le **db_source** attribut appliqué à ce dernier (voir exemple 1). Lorsque vous utilisez **db_source** inline dans une implémentation de méthode, *nom* est une variable (local à la méthode) qui peut être utilisée pour accéder aux données source (voir l’exemple 2). Vous la transmettre *nom* à la *source_name* paramètre de `db_command` pour associer la source de données avec une commande.

*HRESULT*<br/>
(Facultatif) Identifie la variable qui recevra la valeur HRESULT de cette commande de base de données. Si la variable n’existe pas, elle est injectée automatiquement par l’attribut.

## <a name="remarks"></a>Notes

**db_source** crée un [CDataSource](../../data/oledb/cdatasource-class.md) et un [CSession](../../data/oledb/csession-class.md) objet, qui représentent une connexion à une source de données du consommateur OLE DB.

Lorsque vous utilisez **db_source** sur une classe, le `CSession` objet devient un membre de la classe.

Lorsque vous utilisez **db_source** dans une méthode, le code injecté sera exécuté dans la portée de la méthode et le `CSession` objet est créé comme une variable locale.

**db_source** ajoute des propriétés de source de données à une classe ou d’une méthode. Il est utilisé conjointement avec `db_command` (qui prend le *db_source* *nom* paramètre en tant que son *source_name* paramètre).

Lorsque le fournisseur d’attributs consommateur applique cet attribut à une classe, le compilateur renomme la classe à \_ *Nom_de_votre_classe*accesseur, où *Nom_de_votre_classe* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *Nom_de_votre_classe*, qui dérive à son \_ *Nom_de_votre_classe*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.

Pour obtenir un exemple de cet attribut utilisé dans une application, consultez les exemples [AtlAgent](https://github.com/Microsoft/VCSamples) et [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="example"></a>Exemple

Cet exemple appelle **db_source** sur une classe pour créer une connexion à la source de données `ds` à l’aide de la base de données Northwind. `ds` est un handle pour la source de données, ce qui peut être utilisé en interne sur le `CMyCommand` classe.

```cpp
// db_source_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[
  db_source(L"my_connection_string", name="ds"),
  db_command(L"select * from Products")  
]
class CMyCommand {};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**, membre, méthode, locale|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](ole-db-consumer-attributes.md)  
