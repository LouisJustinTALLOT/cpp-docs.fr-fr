---
title: CCommand::GetNextResult | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
dev_langs:
- C++
helpviewer_keywords:
- GetNextResult method
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d833c3e644ac6ed44216542ce4fc6d995cc22efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094193"
---
# <a name="ccommandgetnextresult"></a>CCommand::GetNextResult
Récupère le résultat suivant définir s’il est disponible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,  
   bool bBind = true) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pulRowsAffected*  
 [entrée/sortie] Pointeur vers la mémoire où le nombre de lignes affectées par une commande est retourné.  
  
 `bBind`  
 [in] Spécifie s’il faut lier la commande automatiquement une fois en cours d’exécution. La valeur par défaut est **true**, ce qui entraîne la commande à lier automatiquement. Paramètre `bBind` à **false** empêche la liaison automatique de la commande de sorte que vous pouvez lier manuellement. (Liaison manuelle est particulièrement intéressant pour les utilisateurs OLAP).  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Si un jeu de résultats a été extraite précédemment, cette fonction libère le jeu de résultats précédent et dissocie les colonnes. Si `bBind` est **true**, il lie les nouvelles colonnes.  
  
 Vous devez appeler cette fonction uniquement si vous avez spécifié plusieurs résultats en définissant le `CCommand` paramètre de modèle *TMultiple*=`CMultipleResults`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CCommand, classe](../../data/oledb/ccommand-class.md)