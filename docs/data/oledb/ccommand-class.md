---
title: CCommand (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
dev_langs:
- C++
helpviewer_keywords:
- CCommand class
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 667e86c173a7001ae22036cb1f0dd8f3fbfcf6a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096897"
---
# <a name="ccommand-class"></a>CCommand, classe
Fournit des méthodes pour définir et exécuter une commande.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor,  
          template <typename T> class TRowset = CRowset,  
          class TMultiple = CNoMultipleResults>  
class CCommand :   
           public CAccessorRowset <TAccessor, TRowset>,  
           public CCommandBase,  
           public TMultiple  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TAccessor`  
 Le type de classe de l’accesseur (tel que `CDynamicParameterAccessor`, `CDynamicStringAccessor`, ou `CEnumeratorAccessor`) que vous souhaitez que la commande à utiliser. La valeur par défaut est `CNoAccessor`, ce qui indique que la classe pas prendre en charge des paramètres ou des colonnes de sortie.  
  
 `TRowset`  
 Le type de classe de l’ensemble de lignes (tel que `CArrayRowset` ou `CNoRowset`) que vous souhaitez que la commande à utiliser. La valeur par défaut est `CRowset`.  
  
 `TMultiple`  
 Pour utiliser une commande OLE DB qui peut retourner plusieurs résultats, spécifiez [CMultipleResults](../../data/oledb/cmultipleresults-class.md). Sinon, utilisez [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Pour plus d’informations, consultez [IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx).  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[Fermer](../../data/oledb/ccommand-close.md)|Ferme la commande actuelle.|  
|[GetNextResult](../../data/oledb/ccommand-getnextresult.md)|Récupère le résultat suivant lors de l’utilisation de plusieurs résultats.|  
|[Ouvrir](../../data/oledb/ccommand-open.md)|S’exécute et éventuellement lie la commande.|  
  
### <a name="inherited-methods"></a>Méthodes héritées  
  
|||  
|-|-|  
|[Créer](../../data/oledb/ccommand-create.md)|Crée une nouvelle commande pour la session spécifiée, puis définit le texte de commande.|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|Crée une nouvelle commande.|  
|[GetParameterInfo](../../data/oledb/ccommand-getparameterinfo.md)|Obtient une liste de paramètres de la commande, leurs noms et leurs types.|  
|[Préparer](../../data/oledb/ccommand-prepare.md)|Valide et optimise la commande actuelle.|  
|[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)|Libère l’accesseur de paramètre, si nécessaire, puis libère de la commande.|  
|[SetParameterInfo](../../data/oledb/ccommand-setparameterinfo.md)|Spécifie le type natif de chaque paramètre de commande.|  
|[Annulation de préparation](../../data/oledb/ccommand-unprepare.md)|Ignore le plan d’exécution de commande en cours.|  
  
## <a name="remarks"></a>Notes  
 Utilisez cette classe lorsque vous avez besoin effectuer une opération basée sur un paramètre ou exécuter une commande. Si vous devez simplement ouvrir un ensemble de lignes simple, utilisez [CTable](../../data/oledb/ctable-class.md) à la place.  
  
 La classe d’accesseur que vous utilisez détermine la méthode de liaison des paramètres et des données.  
  
 Notez que vous ne pouvez pas utiliser les procédures stockées avec le fournisseur OLE DB pour Jet car ce fournisseur ne prend pas en charge les procédures (seules des constantes sont autorisées dans les chaînes de requête).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)