---
title: CUtlProps::OnPropertyChanged | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
dev_langs:
- C++
helpviewer_keywords:
- OnPropertyChanged method
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c9b52949db714206b6118000d004c6248b7d6235
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100497"
---
# <a name="cutlpropsonpropertychanged"></a>CUtlProps::OnPropertyChanged
Appelé après la définition d’une propriété de gérer des propriétés chaînées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iCurSet`  
 L’index dans le tableau de jeu de propriétés ; zéro s’il existe une seule propriété ensemble.  
  
 `pDBProp`  
 L’ID de propriété et la nouvelle valeur dans un [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) structure.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard. La valeur par défaut valeur de retour est `S_OK`.  
  
## <a name="remarks"></a>Notes  
 Si vous souhaitez gérer des propriétés chaînées, telles que les signets ou des mises à jour dont les valeurs dépendent de la valeur de la propriété à un autre, vous devez substituer cette fonction.  
  
## <a name="example"></a>Exemple  
 Dans cette fonction, l’utilisateur obtient l’ID de propriété à partir de la `DBPROP*` paramètre. À présent, il est possible comparer l’identificateur par rapport à une propriété de chaîne. Lorsque la propriété est trouvée, `SetProperties` est appelée avec la propriété dont la valeur est maintenant en conjonction avec l’autre propriété. Dans ce cas, si un Obtient le `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, ou `DBPROP_ORDEREDBOOKMARKS` propriété, peut définir le `DBPROP_BOOKMARKS` propriété.  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [CUtlProps, classe](../../data/oledb/cutlprops-class.md)