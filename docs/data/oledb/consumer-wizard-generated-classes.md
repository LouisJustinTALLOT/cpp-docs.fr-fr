---
title: Classes de consommateur générées par l’Assistant
ms.date: 10/17/2018
helpviewer_keywords:
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- command classes in OLE DB consumer
- classes [C++], OLE DB Consumer Wizard-generated
- consumer wizard-generated classes and methods
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
ms.openlocfilehash: 7cd1fbe69186a2fcdbf25f1b2aa12727c98065da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362233"
---
# <a name="consumer-wizard-generated-classes"></a>Classes de consommateur générées par l’Assistant

Lorsque vous utilisez le **Assistant Consommateur OLE DB ATL** pour générer un consommateur, vous avez le choix de l’utilisation de modèles OLE DB et attributs OLE DB. Dans les deux cas, l’Assistant génère une classe de commande et une classe d’enregistrement utilisateur. La classe de commande contient du code destiné à ouvrir la source de données et le rowset que vous avez spécifié dans l’Assistant. La classe d’enregistrement utilisateur contient un mappage de colonnes pour la table de base de données que vous avez sélectionnée. Cependant, le code généré est différent dans chaque cas :

- Si vous sélectionnez un consommateur basé sur un modèle, l’Assistant génère une classe de commande et une classe d’enregistrement utilisateur. La classe de commande aura le nom que vous entrez dans le **classe** zone dans l’Assistant (par exemple, `CProducts`), et la classe d’enregistrement utilisateur aura un nom sous la forme «*ClassName*accesseur » (par exemple, `CProductsAccessor`). Les deux classes sont placées dans le fichier d’en-tête du consommateur.

- Si vous sélectionnez un consommateur avec attributs, la classe d’enregistrement utilisateur prend un nom sous la forme « _*NomClasse*Accessor » avant d’être injectée. Autrement dit, vous serez en mesure d’afficher uniquement la classe de commande dans l’éditeur de texte ; Vous pouvez uniquement afficher la classe d’enregistrement utilisateur en tant que code injecté. Pour plus d’informations sur l’affichage de code injecté, consultez [Débogage de code injecté](/visualstudio/debugger/how-to-debug-injected-code).

Les exemples suivants utilisent une classe de commande créée sur le `Products` table de la `Northwind` base de données pour illustrer le code de consommateur générées par l’Assistant pour la classe de commande et de la classe d’enregistrement utilisateur.

## <a name="templated-user-record-classes"></a>Classes d’enregistrement utilisateur basées sur un modèle

Si vous créez un consommateur OLE DB à l’aide des modèles OLE DB (et non des attributs OLE DB), l’Assistant génère du code comme décrit dans cette section.

### <a name="column-data-members"></a>Membres de données de colonne

La première partie de la classe d’enregistrement utilisateur comprend les déclarations des membres de données et les membres de données d’état et de longueur pour chaque colonne liée aux données. Pour plus d’informations sur ces membres de données, consultez [Membres de données d’état des champs dans les accesseurs générés par l’Assistant](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

> [!NOTE]
> Si vous modifiez la classe d’enregistrement utilisateur ou écrivez votre propre consommateur, les variables de données doivent précéder les variables d’état et de longueur.

> [!NOTE]
> L’Assistant Consommateur OLE DB ATL utilise le `DB_NUMERIC` type pour lier les types de données numériques. Auparavant, il utilisait `DBTYPE_VARNUMERIC` (dont le format est décrit par le `DB_VARNUMERIC` type ; voir Oledb.h). Si vous n’utilisez pas l’Assistant pour créer des consommateurs, il est recommandé d’utiliser `DB_NUMERIC`.

```cpp
// Products.H : Declaration of the CProducts class

class CProductsAccessor
{
public:
   // Column data members:
   LONG m_ProductID;
   TCHAR m_ProductName[41];
   LONG m_SupplierID;
   LONG m_CategoryID;
   TCHAR m_QuantityPerUnit[21];
   CURRENCY m_UnitPrice;
   SHORT m_UnitsInStock;
   SHORT m_UnitsOnOrder;
   SHORT m_ReorderLevel;
   VARIANT_BOOL m_Discontinued;

   // Column status data members:
   DBSTATUS m_dwProductIDStatus;
   DBSTATUS m_dwProductNameStatus;
   DBSTATUS m_dwSupplierIDStatus;
   DBSTATUS m_dwCategoryIDStatus;
   DBSTATUS m_dwQuantityPerUnitStatus;
   DBSTATUS m_dwUnitPriceStatus;
   DBSTATUS m_dwUnitsInStockStatus;
   DBSTATUS m_dwUnitsOnOrderStatus;
   DBSTATUS m_dwReorderLevelStatus;
   DBSTATUS m_dwDiscontinuedStatus;

   // Column length data members:
   DBLENGTH m_dwProductIDLength;
   DBLENGTH m_dwProductNameLength;
   DBLENGTH m_dwSupplierIDLength;
   DBLENGTH m_dwCategoryIDLength;
   DBLENGTH m_dwQuantityPerUnitLength;
   DBLENGTH m_dwUnitPriceLength;
   DBLENGTH m_dwUnitsInStockLength;
   DBLENGTH m_dwUnitsOnOrderLength;
   DBLENGTH m_dwReorderLevelLength;
   DBLENGTH m_dwDiscontinuedLength;
```

### <a name="rowset-properties"></a>Propriétés du rowset

Ensuite, l’Assistant définit les propriétés du rowset. Si vous avez sélectionné **Modifier**, **Insérer**ou **Supprimer** dans l’Assistant Consommateur OLE DB ATL, les propriétés appropriées sont définies ici (DBPROP_IRowsetChange est toujours défini, puis une ou plusieurs propriétés parmi DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT et/ou DBPROPVAL_UP_DELETE, respectivement).

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="command-or-table-class"></a>Classe de commande ou de table

Si vous spécifiez une classe de commande, l’Assistant déclare la classe de commande ; pour le code basé sur un modèle, la commande se présente comme suit :

```cpp
DEFINE_COMMAND_EX(CProductsAccessor, L" \
SELECT \
   ProductID, \
   ProductName, \
   SupplierID, \
   CategoryID, \
   QuantityPerUnit, \
   UnitPrice, \
   UnitsInStock, \
   UnitsOnOrder, \
   ReorderLevel, \
   Discontinued \
   FROM dbo.Products")
```

### <a name="column-map"></a>Mappage de colonnes

L’Assistant génère ensuite les liaisons de colonnes ou le mappage de colonnes. Pour corriger plusieurs problèmes rencontrés avec certains fournisseurs, le code ci-dessous peut lier les colonnes dans un ordre différent de celui indiqué par le fournisseur.

```cpp
   BEGIN_COLUMN_MAP(CProductsAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_SupplierID, m_dwSupplierIDLength, m_dwSupplierIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(4, m_CategoryID, m_dwCategoryIDLength, m_dwCategoryIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(5, m_QuantityPerUnit, m_dwQuantityPerUnitLength, m_dwQuantityPerUnitStatus)
      _COLUMN_ENTRY_CODE(6, DBTYPE_CY, _SIZE_TYPE(m_UnitPrice), 0, 0, offsetbuf(m_UnitPrice), offsetbuf(m_dwUnitPriceLength), offsetbuf(m_dwUnitPriceStatus))
      COLUMN_ENTRY_LENGTH_STATUS(7, m_UnitsInStock, m_dwUnitsInStockLength, m_dwUnitsInStockStatus)
      COLUMN_ENTRY_LENGTH_STATUS(8, m_UnitsOnOrder, m_dwUnitsOnOrderLength, m_dwUnitsOnOrderStatus)
      COLUMN_ENTRY_LENGTH_STATUS(9, m_ReorderLevel, m_dwReorderLevelLength, m_dwReorderLevelStatus)
      _COLUMN_ENTRY_CODE(10, DBTYPE_BOOL, _SIZE_TYPE(m_Discontinued), 0, 0, offsetbuf(m_Discontinued), offsetbuf(m_dwDiscontinuedLength), offsetbuf(m_dwDiscontinuedStatus))
   END_COLUMN_MAP()
};
```

### <a name="class-declaration"></a>Déclaration de classe

Enfin, l’Assistant génère une déclaration de classe de commande semblable à la suivante :

```cpp
class CProducts : public CCommand<CAccessor<CProductsAccessor>>
```

## <a name="attribute-injected-user-record-classes"></a>Classes d'enregistrement utilisateur injectées par les attributs

Si vous créez un consommateur OLE DB en utilisant les attributs de base de données ([db_command](../../windows/db-command.md) ou [db_table](../../windows/db-table.md)), les attributs injectent une classe d’enregistrement utilisateur dont le nom prend la forme « _*NomClasse*Accessor ». Par exemple, si vous avez nommé votre classe de commande `COrders`, la classe d’enregistrement utilisateur s’intitule `_COrdersAccessor`. Bien que la classe d’enregistrement utilisateur s’affiche dans **affichage de classes**, en double-cliquant dessus accède à la classe de commande ou de table dans le fichier d’en-tête à la place. Dans ce cas, vous ne pouvez voir la déclaration réelle de la classe d’enregistrement utilisateur qu’en affichant le code injecté par les attributs.

Vous pouvez rencontrer des complications si vous ajoutez ou substituez des méthodes dans des consommateurs avec attributs. Par exemple, vous pouvez décider d’ajouter un constructeur `_COrdersAccessor` à la déclaration `COrders` . Or, en réalité, le constructeur est ajouté à la classe `COrdersAccessor` injectée. Ce constructeur peut initialiser les colonnes/paramètres, mais vous ne pouvez pas créer un constructeur de copie de cette façon, car il ne peut pas instancier directement le `COrdersAccessor` objet. Si vous avez besoin d’un constructeur (ou autre méthode) directement sur le `COrders` (classe), il est recommandé que vous définissez une nouvelle classe dérivant de `COrders` et ajoutez les méthodes nécessaires.

Dans l’exemple suivant, l’Assistant génère une déclaration pour la classe `COrders`, mais la classe d’enregistrement utilisateur `COrdersAccessor` n’apparaît pas, car elle est injectée par les attributs.

```cpp
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>
[
   db_source(L"your connection string"),
   db_command(L"Select ShipName from Orders;")
]
class COrders
{
public:

   // COrders()            // incorrect constructor name
   _COrdersAccessor()      // correct constructor name
   {
   }
      [db_column(1) ] TCHAR m_ShipName[41];
   };
```

La déclaration de classe de commande injectée se présente comme ceci :

```cpp
class CProducts : public CCommand<CAccessor<_CProductsAccessor>>
```

Le code injecté est pour l’essentiel identique ou similaire à la version basée sur un modèle. Les principales différences résident dans les méthodes injectées, qui sont décrites dans [Méthodes générées par l’Assistant Consommateur](../../data/oledb/consumer-wizard-generated-methods.md).

Pour plus d’informations sur l’affichage de code injecté, consultez [Débogage de code injecté](/visualstudio/debugger/how-to-debug-injected-code).

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB en utilisant l’Assistant](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)