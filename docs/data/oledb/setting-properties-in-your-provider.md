---
title: Définition de propriétés dans votre fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 2cbb334ab15912fdcf6980461016976d869f5a84
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029458"
---
# <a name="setting-properties-in-your-provider"></a>Définition de propriétés dans votre fournisseur

Recherchez le groupe de propriétés et l’ID de propriété pour la propriété qui que vous intéresse. Pour plus d’informations, consultez [propriétés OLE DB](/previous-versions/windows/desktop/ms722734(v=vs.85)) dans le **de référence du programmeur OLE DB**.

Dans le code du fournisseur généré par l’Assistant, recherchez le mappage des propriétés correspondant au groupe de propriétés. Le nom du groupe de propriétés correspond généralement au nom de l’objet. Propriétés Command et rowset figurent dans la commande ou l’ensemble de lignes ; Vous trouverez les propriétés source et de l’initialisation des données dans l’objet de source de données.

Dans le mappage des propriétés, ajoutez un [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) macro. PROPERTY_INFO_ENTRY_EX prend quatre paramètres :

- L’ID de propriété correspondant à votre propriété. Supprimer les sept premiers caractères (« DBPROP_ ») du début du nom de la propriété. Par exemple, si vous souhaitez ajouter `DBPROP_MAXROWS`, transmettez `MAXROWS` comme premier élément. S’il s’agit d’une propriété personnalisée, passez le nom complet de GUID (par exemple, `DBMYPROP_MYPROPERTY`).

- Le type variant de la propriété (dans [propriétés OLE DB](/previous-versions/windows/desktop/ms722734(v=vs.85)) dans le **de référence du programmeur OLE DB**). Entrez le type (par exemple, VT_BOOL ou VT_I2) VT_ correspondant au type de données.

- Indicateurs pour indiquer si la propriété est accessible en lecture et en écriture et le groupe auquel il appartient. Par exemple, le code suivant indique une propriété en lecture/écriture appartenant au groupe de l’ensemble de lignes :

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- La valeur de la propriété de base. Cela peut être `VARIANT_FALSE` pour une valeur booléenne tapez, ou zéro pour un type entier, par exemple. La propriété a cette valeur, sauf si elle est modifiée.

    > [!NOTE]
    > Certaines propriétés sont connectées ou chaînées à d’autres propriétés, telles que les signets ou la mise à jour. Quand un consommateur définit une propriété sur true, une autre propriété peut également être définie. Les modèles du fournisseur OLE DB prennent en charge via la méthode [CUtlProps::OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Propriétés ignorées par les fournisseurs Microsoft OLE DB

Les fournisseurs OLE DB ignorer les propriétés OLE DB suivantes :

- `DBPROP_MAXROWS` fonctionne uniquement pour les fournisseurs en lecture seule (autrement dit, où `DBPROP_IRowsetChange` et `DBPROP_IRowsetUpdate` sont **false**) ; sinon, cette propriété n’est pas pris en charge.

- `DBPROP_MAXPENDINGROWS` est ignoré ; le fournisseur spécifie sa propre limite.

- `DBPROP_MAXOPENROWS` est ignoré ; le fournisseur spécifie sa propre limite.

- `DBPROP_CANHOLDROWS` est ignoré ; le fournisseur spécifie sa propre limite.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)