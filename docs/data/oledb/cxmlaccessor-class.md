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
ms.openlocfilehash: f25fb3635f70ee9a0e38ddcdbcf373fe6b1b84c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211040"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor, classe

Vous permet d’accéder aux sources de données en tant que données de chaîne lorsque vous n’avez aucune connaissance du schéma de la Banque de données (structure sous-jacente).

## <a name="syntax"></a>Syntaxe

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Spécifications

**En-tête**: atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|Récupère les informations de colonne.|
|[GetXMLRowData](#getxmlrowdata)|Récupère la totalité du contenu d’une table par lignes.|

## <a name="remarks"></a>Notes

Toutefois, `CXMLAccessor` diffère de `CDynamicStringAccessorW` dans la mesure où elle convertit toutes les données accessibles depuis le magasin de données en tant que données au format XML (balisées). Cela s’avère particulièrement utile pour la sortie vers des pages Web compatibles avec XML. Les noms de balises XML correspondent le plus fidèlement possible aux noms de colonnes de la Banque de données.

Utilisez `CDynamicAccessor` méthodes pour obtenir des informations sur les colonnes. Vous utilisez ces informations de colonne pour créer un accesseur de manière dynamique au moment de l’exécution.

Les informations de colonne sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenir des informations sur les colonnes à l’aide de [GetXMLColumnData](#getxmlcolumndata) ou obtenir des données de colonne par lignes à l’aide de [GetXMLRowData](#getxmlrowdata).

## <a name="example"></a>Exemple

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="cxmlaccessorgetxmlcolumndata"></a><a name="getxmlcolumndata"></a>CXMLAccessor :: GetXMLColumnData

Récupère les informations sur le type de colonne d’une table en tant que données de chaîne au format XML, par colonne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Paramètres

*strOutput*<br/>
à Référence à une mémoire tampon de chaîne contenant les informations de type de colonne à récupérer. La chaîne est mise en forme avec des noms de balise XML qui correspondent aux noms de colonnes de la Banque de données.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

L’exemple suivant montre comment les informations sur le type de colonne sont formatées en XML. `type` spécifie le type de données de la colonne. Notez que les types de données sont basés sur les types de données OLE DB, et non sur ceux de la base de données qui fait l’objet de l’accès.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="cxmlaccessorgetxmlrowdata"></a><a name="getxmlrowdata"></a>CXMLAccessor :: GetXMLRowData

Récupère la totalité du contenu d’une table en tant que données de chaîne au format XML, par ligne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Paramètres

*strOutput*<br/>
à Référence à une mémoire tampon contenant les données de table à récupérer. Les données sont mises en forme en tant que données de chaîne avec des noms de balise XML qui correspondent aux noms de colonnes de la Banque de données.

*bAppend*<br/>
dans Valeur booléenne qui spécifie s’il faut ajouter une chaîne à la fin des données de sortie.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

L’exemple suivant montre comment les données de ligne sont mises en forme au format XML. `DATA` ci-dessous représente les données de ligne. Utilisez les méthodes Move pour passer à la ligne souhaitée.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor, classe](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA, classe](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW, classe](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)
