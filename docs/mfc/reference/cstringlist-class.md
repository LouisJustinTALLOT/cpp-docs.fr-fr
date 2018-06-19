---
title: Classe de CStringList | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91a88fc73b27323327bce477fa2cdaca747ed21c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375146"
---
# <a name="cstringlist-class"></a>Classe de CStringList
Prend en charge des listes d'objets `CString` .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStringList : public CObject  
```  
  
## <a name="members"></a>Membres  
 Les fonctions membres de `CStringList` sont similaires aux fonctions membres de classe [CObList](../../mfc/reference/coblist-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObList` pour connaître les spécificités des fonctions membres. Chaque fois que vous voyez un `CObject` pointeur en tant que valeur de retour, remplacez un `CString` (pas un `CString` pointeur). Chaque fois que vous voyez un `CObject` pointeur en tant que paramètre de fonction, remplacez un `LPCTSTR`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 par exemple, se traduit par  
  
 `CString& CStringList::GetHead() const;`  
  
 et  
  
 `POSITION AddHead( CObject* <newElement> );`  
  
 se traduit par  
  
 `POSITION AddHead( LPCTSTR <newElement> );`  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|Construit une liste vide.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Ajoute un élément (ou tous les éléments dans une autre liste) au début de la liste (fait une nouvelle tête).|  
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|Ajoute un élément (ou tous les éléments dans une autre liste) à la fin de la liste (fait une nouvelle fin).|  
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|Obtient la position d’un élément spécifié par la valeur du pointeur.|  
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|Obtient la position d’un élément spécifié par un index de base zéro.|  
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|Obtient l’élément à une position donnée.|  
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|Retourne le nombre d’éléments dans cette liste.|  
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Retourne l’élément principal de la liste (ne peut pas être vide).|  
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Retourne la position de l’élément principal de la liste.|  
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|Obtient l’élément suivant pour une itération.|  
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Obtient l’élément précédent pour une itération.|  
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|Retourne le nombre d’éléments dans cette liste.|  
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|  
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Retourne la position de l’élément de fin de la liste.|  
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Insère un nouvel élément après une position donnée.|  
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Insère un élément avant une position donnée.|  
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Vérifie si la condition de liste vide (aucun élément).|  
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Supprime tous les éléments de cette liste.|  
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Supprime un élément de cette liste, spécifiée par position.|  
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Supprime l’élément de la tête de la liste.|  
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Supprime l’élément de la fin de la liste.|  
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|Définit l’élément à une position donnée.|  
  
## <a name="remarks"></a>Notes  
 Toutes les comparaisons sont effectuées par valeur, qui signifie que les caractères de la chaîne sont comparés à la place les adresses des chaînes.  
  
 `CStringList` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Si une liste de `CString` objets est stocké dans une archive, avec un opérateur d’insertion surchargés ou avec le `Serialize` fonction membre, chaque `CString` élément est sérialisé à son tour.  
  
 Si vous avez besoin d’un vidage de personne `CString` éléments, vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.  
  
 Pour plus d’informations sur l’utilisation de `CStringList`, consultez l’article [Collections](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxcoll.h  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC COLLECT](../../visual-cpp-samples.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



