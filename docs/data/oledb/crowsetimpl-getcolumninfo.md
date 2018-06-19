---
title: CRowsetImpl::GetColumnInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a989b31d672c9019d2ed5e61490f4e0042ab4c47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096465"
---
# <a name="crowsetimplgetcolumninfo"></a>CRowsetImpl::GetColumnInfo
Récupère les informations de colonne pour une demande de client particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,  
   ULONG* pcCols);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pv`  
 [in] Un pointeur vers l’utilisateur `CRowsetImpl` classe dérivée.  
  
 `pcCols`  
 [in] Un pointeur (sortie) au nombre de colonnes retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un statique **ATLCOLUMNINFO** structure.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est un remplacement avancé.  
  
 Cette méthode est appelée par plusieurs classes d’implémentation de base pour récupérer les informations de colonne pour une demande de client particulier. En règle générale, cette méthode appelée `IColumnsInfoImpl`. Si vous substituez cette méthode, vous devez placer une version de la méthode dans votre `CRowsetImpl`-classe dérivée. Étant donné que la méthode peut être placée dans une classe non transformer en modèle, vous devez modifier `pv` approprié `CRowsetImpl`-classe dérivée.  
  
 L’exemple suivant montre comment **de GetColumnInfo** utilisation. Dans cet exemple, **CMyRowset** est un `CRowsetImpl`-classe dérivée. Afin de pouvoir remplacer `GetColumnInfo` pour toutes les instances de cette classe, placez la méthode suivante dans le **CMyRowset** définition de classe :  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRowsetImpl, classe](../../data/oledb/crowsetimpl-class.md)