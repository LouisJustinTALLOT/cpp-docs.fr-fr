---
title: CRowset::UpdateAll | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset::UpdateAll
- ATL.CRowset.UpdateAll
- CRowset<TAccessor>.UpdateAll
- ATL.CRowset<TAccessor>.UpdateAll
- UpdateAll
- CRowset.UpdateAll
- ATL::CRowset<TAccessor>::UpdateAll
- CRowset<TAccessor>::UpdateAll
- ATL::CRowset::UpdateAll
dev_langs:
- C++
helpviewer_keywords:
- UpdateAll method
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9e21cd34a4d758becb12b529fe858e96d18f187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092189"
---
# <a name="crowsetupdateall"></a>CRowset::UpdateAll
Transmet toutes les modifications apportées à toutes les lignes depuis la dernière extraction ou **mise à jour** appeler sur celle-ci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT UpdateAll(DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcRows`  
 [out] Un pointeur vers l’emplacement où `UpdateAll` retourne le nombre de lignes qu’il a tenté de mettre à jour, si nécessaire.  
  
 `pphRow`  
 [out] Pointeur vers la mémoire dans lequel `UpdateAll` retourne le handle de la ligne, il avait tenté de mettre à jour. Aucun handle n’est retournée si `pphRow` a la valeur null.  
  
 `ppStatus`  
 [out] Un pointeur vers l’emplacement où **mise à jour** retourne la valeur d’état de ligne. Aucun état n’est retournée si `ppStatus` a la valeur null.  
  
## <a name="remarks"></a>Notes  
 Transmet toutes les modifications apportées à toutes les lignes depuis ces lignes ont été dernière extraction ou mises à jour avec [mise à jour](../../data/oledb/crowset-update.md) ou `UpdateAll`. `UpdateAll` met à jour chaque ligne qui a été modifié, indépendamment de si vous avez toujours le handle pour eux (voir `pphRow`) ou non.  
  
 Par exemple, si vous avez utilisé **insérer** pour insérer cinq lignes dans un ensemble de lignes, vous pouvez appeler **mettre à jour** cinq fois ou appelez `UpdateAll` une fois pour mettre à jour toutes les.  
  
 Cette méthode requiert l’interface facultative `IRowsetUpdate`, qui ne peut pas être pris en charge sur tous les fournisseurs ; si c’est le cas, la méthode retourne **E_NOINTERFACE**. Vous devez également définir **DBPROP_IRowsetUpdate** à `VARIANT_TRUE` avant d’appeler **ouvrir** sur la table ou d’une commande qui contient l’ensemble de lignes.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRowset (classe)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)