---
title: Enregistrements utilisateur
ms.date: 05/09/2019
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
ms.openlocfilehash: c9c1126f0e8248f31ac739bb1d939f811bda678d
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525286"
---
# <a name="user-records"></a>Enregistrements utilisateur

> [!NOTE]
> L’Assistant Consommateur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures. Vous pouvez toujours ajouter la fonctionnalité manuellement. Pour plus d’informations, consultez [Création d’un consommateur sans utiliser l’Assistant](creating-a-consumer-without-using-a-wizard.md).

Pour utiliser un accesseur statique (c’est-à-dire un accesseur dérivé de `CAccessor`), le consommateur doit disposer d’un enregistrement utilisateur. L’enregistrement utilisateur est une classe C++ qui contient les éléments de données pour gérer les entrées-sorties. L’**Assistant Consommateur OLE DB ATL** génère un enregistrement utilisateur pour votre consommateur. Vous pouvez ajouter des méthodes à l’enregistrement utilisateur pour des tâches facultatives telles que la gestion des commandes.

Le code suivant montre un exemple d’enregistrement qui gère les commandes. Dans l’enregistrement utilisateur, BEGIN_COLUMN_MAP représente un ensemble de lignes de données passé au consommateur depuis un fournisseur. BEGIN_PARAM_MAP représente un ensemble de paramètres de commande. Cet exemple utilise une classe [CCommand](../../data/oledb/ccommand-class.md) pour gérer les paramètres de commande. Les membres de données dans les entrées de mappage représentent des décalages dans un bloc contigu de mémoire pour chaque instance de la classe. Les macros COLUMN_ENTRY correspondent aux macros PROVIDER_COLUMN_ENTRY côté fournisseur.

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

## <a name="wizard-generated-user-records"></a>Enregistrements utilisateur générés par l’Assistant

Quand vous utilisez l’**Assistant Consommateur OLE DB ATL** pour générer un consommateur, vous pouvez utiliser soit des modèles OLE DB, soit des attributs OLE DB. Le code généré varie selon le cas. Pour plus d’informations sur ce code, consultez [Classes de consommateur générées par l’Assistant](../../data/oledb/consumer-wizard-generated-classes.md).

## <a name="user-record-support-for-multiple-accessors"></a>Prise en charge des enregistrements utilisateur pour plusieurs accesseurs

Pour obtenir une présentation détaillée des scénarios dans lesquels vous auriez à utiliser plusieurs accesseurs, consultez [Utilisation de plusieurs accesseurs dans un ensemble de lignes](../../data/oledb/using-multiple-accessors-on-a-rowset.md).

L’exemple suivant montre l’enregistrement utilisateur modifié pour prendre en charge plusieurs accesseurs dans l’ensemble de lignes. Au lieu de BEGIN_COLUMN_MAP et END_COLUMN_MAP, il utilise [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) et [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) pour chaque accesseur. La macro BEGIN_ACCESSOR spécifie le numéro de l’accesseur (décalage partant de zéro) et indique si l’accesseur est un auto-accesseur. Les auto-accesseurs appellent `GetData` pour récupérer les données automatiquement via un appel à [MoveNext](../../data/oledb/crowset-movenext.md). Les accesseurs non automatiques nécessitent que vous récupériez explicitement les données. Utilisez un accesseur non automatique si vous effectuez une liaison vers un champ de données de grande taille (par exemple, une image bitmap) que vous ne voulez pas récupérer pour chaque enregistrement.

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

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)