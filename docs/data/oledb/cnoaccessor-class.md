---
title: Cnoaccessor, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
dev_langs:
- C++
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3110d20330d42fcb0816873ff3e8a25d1f8436ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097352"
---
# <a name="cnoaccessor-class"></a>CNoAccessor, classe
Peut être utilisé comme argument de modèle (`TAccessor`) pour les classes de modèle, telles que `CCommand` et `CTable`, qui nécessitent un argument de classe d’accesseur.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CNoAccessor  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez `CNoAccessor` comme argument de modèle lorsque vous ne souhaitez pas la classe pour prendre en charge des paramètres ou des colonnes de sortie.  
  
 `CNoAccessor` implémente les méthodes stub suivantes, chacune d’elles correspondent aux autres méthodes d’accesseur de classe :  
  
-   **BindColumns** -lie les colonnes aux accesseurs.  
  
-   `BindParameters` -Lie les paramètres aux colonnes.  
  
-   **Lier** -crée des liaisons.  
  
-   **Fermer** -ferme l’accesseur.  
  
-   `ReleaseAccessors` -Libère les accesseurs créés par la classe.  
  
-   `FreeRecordMemory` -Permet de libérer toutes les colonnes dans l’enregistrement actif qui doivent être libérées.  
  
-   `GetColumnInfo` -Obtient les informations de colonne à partir de l’ensemble de lignes ouvert.  
  
-   `GetNumAccessors` -Récupère le nombre d’accesseurs créé par la classe.  
  
-   `IsAutoAccessor` -Retourne la valeur true si les données sont récupérées automatiquement pour l’accesseur pendant une opération de déplacement.  
  
-   `GetHAccessor` -Récupère le handle d’accesseur d’un accesseur spécifié.  
  
-   `GetBuffer` -Récupère le pointeur vers la mémoire tampon de signet.  
  
-   **NoBindOnNullRowset** -empêche la liaison de données sur des ensembles de lignes vide.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)