---
title: Définition de propriétés dans votre fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 3717282d284990b1b8038f6954ee971938cf7921
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509476"
---
# <a name="setting-properties-in-your-provider"></a>Définition de propriétés dans votre fournisseur

Recherchez le groupe de propriétés et l’ID de propriété de la propriété souhaitée. Pour plus d’informations, consultez [OLE DB Properties](/previous-versions/windows/desktop/ms722734(v=vs.85)) dans le **Guide de référence du programmeur OLE DB**.

Dans le code du fournisseur généré par l’Assistant, recherchez le mappage des propriétés correspondant au groupe de propriétés. Le nom du groupe de propriétés correspond généralement au nom de l’objet. Les propriétés de commande et d’ensemble de lignes se trouvent dans la commande ou l’ensemble de lignes. la source de données et les propriétés d’initialisation se trouvent dans l’objet source de données.

Dans le mappage des propriétés, ajoutez une macro [PROPERTY_INFO_ENTRY_EX](./macros-for-ole-db-provider-templates.md#property_info_entry_ex) . PROPERTY_INFO_ENTRY_EX prend quatre paramètres :

- ID de propriété correspondant à votre propriété. Supprimez les sept premiers caractères (« DBPROP_ ») du début du nom de la propriété. Par exemple, si vous souhaitez ajouter `DBPROP_MAXROWS` , transmettez `MAXROWS` en tant que premier élément. S’il s’agit d’une propriété personnalisée, transmettez le nom GUID complet (par exemple, `DBMYPROP_MYPROPERTY` ).

- Type variant de la propriété (dans [OLE DB propriétés](/previous-versions/windows/desktop/ms722734(v=vs.85)) dans le **OLE DB Guide de référence du programmeur**). Entrez le type de VT_ (par exemple, VT_BOOL ou VT_I2) correspondant au type de données.

- Indicateurs pour indiquer si la propriété est accessible en lecture et en écriture et le groupe auquel elle appartient. Par exemple, le code suivant indique une propriété en lecture/écriture qui appartient au groupe d’ensembles de lignes :

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- Valeur de base de la propriété. Il peut s’agir `VARIANT_FALSE` d’un type booléen ou zéro pour un type entier, par exemple. La propriété a cette valeur, sauf si elle est modifiée.

    > [!NOTE]
    > Certaines propriétés sont connectées ou chaînées à d’autres propriétés, telles que les signets ou la mise à jour. Lorsqu’un consommateur affecte la valeur true à une propriété, une autre propriété peut également être définie. Les modèles du fournisseur OLE DB prennent en charge ce mode via la méthode [CUtlProps :: OnPropertyChanged](./cutlprops-class.md#onpropertychanged).

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Propriétés ignorées par les fournisseurs de OLE DB Microsoft

Les fournisseurs de OLE DB Microsoft ignorent les propriétés de OLE DB suivantes :

- `DBPROP_MAXROWS` fonctionne uniquement pour les fournisseurs en lecture seule (c’est-à-dire, où `DBPROP_IRowsetChange` et `DBPROP_IRowsetUpdate` sont **`false`** ); sinon, cette propriété n’est pas prise en charge.

- `DBPROP_MAXPENDINGROWS` est ignoré ; le fournisseur spécifie sa propre limite.

- `DBPROP_MAXOPENROWS` est ignoré ; le fournisseur spécifie sa propre limite.

- `DBPROP_CANHOLDROWS` est ignoré ; le fournisseur spécifie sa propre limite.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
