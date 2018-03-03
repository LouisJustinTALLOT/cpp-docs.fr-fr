---
title: Classe de CPtrList | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPtrList
dev_langs:
- C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d7e69c8c0d80fea2720ea436bf0bff796ae57a60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cptrlist-class"></a>Classe de CPtrList
Prend en charge des listes de pointeurs void.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPtrList : public CObject  
```  
  
## <a name="members"></a>Membres  
 Les fonctions membres de `CPtrList` sont similaires aux fonctions membres de classe [CObList](../../mfc/reference/coblist-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObList` pour connaître les spécificités des fonctions membres. Chaque fois que vous voyez un `CObject` pointeur en tant que paramètre de fonction ou valeur de retour, remplacez par un pointeur vers `void`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 par exemple, se traduit par  
  
 `void*& CPtrList::GetHead() const;`  
  
## <a name="remarks"></a>Notes  
 `CPtrList`incorpore la `IMPLEMENT_DYNAMIC` macro pour prendre en charge les accès de type au moment de l’exécution et le vidage à un `CDumpContext` objet. Si vous avez besoin d’un vidage de pointeur individuels des éléments de liste, vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.  
  
 Listes de pointeur ne peut pas être sérialisés.  
  
 Lorsqu’un `CPtrList` objet est supprimé, ou lorsque ses éléments sont supprimés, seuls les pointeurs sont supprimées, pas les entités qu’ils référencent.  
  
 Pour plus d’informations sur l’utilisation de `CPtrList`, consultez l’article [Collections](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcoll.h  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CObList, classe](../../mfc/reference/coblist-class.md)
