---
title: Enregistrements utilisateur
ms.date: 10/22/2018
f1_keywords:
- COLUMN_ENTRY_MAP
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
ms.openlocfilehash: 5dd7be3eccd59dc1a5a0dc1cd6932ca1310627c0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041005"
---
# <a name="user-records"></a>Enregistrements utilisateur

Pour utiliser un accesseur statique (autrement dit, un accesseur dérivé `CAccessor`), le consommateur doit disposer d’un enregistrement utilisateur. L’enregistrement de l’utilisateur est une classe C++ qui contient les éléments de données à l’entrée de handle ou de sortie. Le **Assistant Consommateur OLE DB ATL** génère un enregistrement d’utilisateur pour le consommateur. Vous pouvez ajouter des méthodes à l’enregistrement d’utilisateur pour des tâches facultatives telles que la gestion des commandes.

Le code suivant montre un exemple d’enregistrement qui gère les commandes. Dans l’enregistrement utilisateur, BEGIN_COLUMN_MAP représente un ensemble de lignes de données passée au consommateur par un fournisseur. BEGIN_PARAM_MAP représente un ensemble de paramètres de commande. Cet exemple utilise un [CCommand](../../data/oledb/ccommand-class.md) classe pour gérer les paramètres de commande. Les membres de données dans les entrées de mappage représentent des offsets dans un bloc contigu de mémoire pour chaque instance de la classe. Les macros COLUMN_ENTRY correspondent aux macros PROVIDER_COLUMN_ENTRY côté fournisseur.

Pour plus d’informations sur les macros COLUMN_MAP et PARAM_MAP, consultez [Macros pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="wizard-generated-user-records"></a>Enregistrements d’utilisateur générées par l’Assistant

Si vous utilisez le **Assistant Consommateur OLE DB ATL** pour générer un consommateur, vous avez le choix de l’utilisation de modèles OLE DB ou des attributs OLE DB. Le code généré est différent dans chaque cas. Pour plus d’informations sur ce code, consultez [Consumer Wizard-Generated Classes](../../data/oledb/consumer-wizard-generated-classes.md).

## <a name="user-record-support-for-multiple-accessors"></a>Prise en charge pour plusieurs accesseurs des enregistrements utilisateur

Pour obtenir une présentation détaillée des scénarios dans lesquels vous devez utiliser plusieurs accesseurs, consultez [à l’aide de plusieurs accesseurs sur un ensemble de lignes](../../data/oledb/using-multiple-accessors-on-a-rowset.md).

L’exemple suivant montre l’enregistrement utilisateur modifié pour prendre en charge plusieurs accesseurs sur l’ensemble de lignes. Au lieu de BEGIN_COLUMN_MAP et END_COLUMN_MAP, il utilise [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) et [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) pour chaque accesseur. La macro BEGIN_ACCESSOR spécifie le numéro de l’accesseur (offset à partir de zéro) et indique si l’accesseur est un auto-accesseur. Les auto-accesseurs appel `GetData` pour récupérer les données automatiquement via un appel à [MoveNext](../../data/oledb/crowset-movenext.md). Accesseurs non automatiques exigent que vous récupériez explicitement les données. Utilisez un accesseur non automatique si vous effectuez une liaison vers un champ de données de grande taille (par exemple, une image bitmap) que vous ne pouvez pas récupérer pour chaque enregistrement.

```cpp
class CMultiArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor
    COLUMN_ENTRY(1, m_szFirstName)
    COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor
    COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)