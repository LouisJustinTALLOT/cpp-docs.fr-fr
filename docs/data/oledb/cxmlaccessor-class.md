---
title: CXMLAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
ms.openlocfilehash: 1d57251e48f2496b07a4eb4f94976c7a44b165f9
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328511"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor, classe

Permet d’accéder aux sources de données en tant que données de chaîne lorsque vous n’avez aucune connaissance du schéma du magasin de données (structure sous-jacente).

## <a name="syntax"></a>Syntaxe

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Configuration requise

**En-tête**: atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|Récupère les informations de colonne.|
|[GetXMLRowData](#getxmlrowdata)|Récupère le contenu entier d’une table par lignes.|

## <a name="remarks"></a>Notes

Toutefois, `CXMLAccessor` diffère `CDynamicStringAccessorW` car elle convertit toutes les données accédées à partir du magasin de données au format XML (référencé). Cela est particulièrement utile pour la sortie vers des pages Web prenant en charge XML. Les noms de balise XML correspond à des noms de colonnes du magasin de données aussi fidèlement que possible.

Utilisez `CDynamicAccessor` méthodes pour obtenir des informations de colonne. Ces informations de colonne vous permet de créer un accesseur dynamiquement au moment de l’exécution.

Les informations de colonne sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenir des informations de colonne à l’aide [GetXMLColumnData](#getxmlcolumndata) ou obtenir des données de la colonne en lignes à l’aide [GetXMLRowData](#getxmlrowdata).

## <a name="example"></a>Exemple

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="getxmlcolumndata"></a> CXMLAccessor::GetXMLColumnData

Récupère les informations de type de colonne d’une table en tant que données de chaîne au format XML, par colonne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Paramètres

*strOutput*<br/>
[out] Une référence à une mémoire tampon de chaîne qui contient les informations de type de colonne à récupérer. La chaîne est mise en forme avec des noms de balise XML qui correspondent aux noms de colonne du magasin de données.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

L’exemple suivant montre comment les informations de type de colonne sont au format XML. `type` Spécifie le type de données de la colonne. Notez que les types de données sont basés sur les types de données OLE DB, pas celles de la base de données en cours d’accès.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="getxmlrowdata"></a> CXMLAccessor::GetXMLRowData

Récupère le contenu entier d’une table en tant que données de chaîne au format XML, en ligne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Paramètres

*strOutput*<br/>
[out] Une référence à une mémoire tampon contenant les données de table à récupérer. Les données sont formatées en tant que données de chaîne avec les noms de balise XML qui correspondent aux noms de colonne du magasin de données.

*bAppend*<br/>
[in] Valeur booléenne spécifiant s’il faut ajouter une chaîne à la fin des données de sortie.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

L’exemple suivant montre comment les données de ligne sont au format XML. `DATA` ci-dessous représente les données de ligne. Utilisez les méthodes pour passer à la ligne souhaitée de déplacement.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor, classe](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA, classe](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW, classe](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)