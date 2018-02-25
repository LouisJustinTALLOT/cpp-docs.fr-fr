---
title: Enregistrements utilisateur | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_MAP
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: faead3ec85fc799abd26613979f7611c9159cc9b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="user-records"></a>Enregistrements utilisateur
Pour utiliser un accesseur statique (autrement dit, un accesseur dérivé **CAccessor)**, le consommateur doit disposer d’un enregistrement d’utilisateur. L’enregistrement de l’utilisateur est une classe C++ qui contienne les éléments de données à l’entrée de handle ou de sortie. L’Assistant Consommateur OLE DB ATL génère un enregistrement d’utilisateur pour le consommateur. Vous pouvez ajouter des méthodes à l’enregistrement d’utilisateur pour les tâches facultatives telles que la gestion des commandes.  
  
 Le code suivant montre un exemple d’enregistrement qui gère les commandes. Dans l’enregistrement d’utilisateur, `BEGIN_COLUMN_MAP` représente un ensemble de lignes de données passée au consommateur d’un fournisseur. `BEGIN_PARAM_MAP` représente un ensemble de paramètres de commande. Cet exemple utilise un [CCommand](../../data/oledb/ccommand-class.md) classe pour gérer les paramètres de commande. Les membres de données dans les entrées de mappage représentent des offsets dans un bloc contigu de mémoire pour chaque instance de la classe. Le `COLUMN_ENTRY` macros correspondent à la `PROVIDER_COLUMN_ENTRY` macros côté fournisseur.  
  
 Pour plus d’informations sur la **COLUMN_MAP** et **PARAM_MAP** macros, consultez [Macros pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
```  
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
 Si vous utilisez l’Assistant Consommateur OLE DB ATL pour générer un consommateur, vous avez le choix de l’utilisation de modèles OLE DB et attributs OLE DB. Le code généré est différent dans chaque cas. Pour plus d’informations sur ce code, consultez [Consumer Wizard-Generated Classes](../../data/oledb/consumer-wizard-generated-classes.md).  
  
## <a name="user-record-support-for-multiple-accessors"></a>Prise en charge enregistrement d’utilisateur pour les accesseurs multiples  
 Pour obtenir une présentation détaillée des scénarios dans lesquels vous devez utiliser plusieurs accesseurs, consultez [à l’aide de plusieurs accesseurs sur un ensemble de lignes](../../data/oledb/using-multiple-accessors-on-a-rowset.md).  
  
 L’exemple suivant montre l’enregistrement utilisateur modifié pour prendre en charge plusieurs accesseurs sur l’ensemble de lignes. Au lieu de `BEGIN_COLUMN_MAP` et `END_COLUMN_MAP`, il utilise [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) et [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) pour chaque accesseur. Le `BEGIN_ACCESSOR` macro Spécifie le numéro de l’accesseur (offset à partir de zéro) et indique si l’accesseur est un auto-accesseur. Les auto-accesseurs appel `GetData` pour récupérer les données automatiquement via un appel à [MoveNext](../../data/oledb/crowset-movenext.md). Accesseurs non automatiques exigent explicitement extraire les données. Utilisez un accesseur non automatique si vous établissez une liaison à un champ de données de grande taille (par exemple, une image bitmap) que vous pouvez récupérer pour chaque enregistrement.  
  
```  
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