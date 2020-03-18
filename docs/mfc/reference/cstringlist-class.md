---
title: CStringList, classe
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CStringList::CStringList
- AFXCOLL/CStringList::AddHead
- AFXCOLL/CStringList::AddTail
- AFXCOLL/CStringList::Find
- AFXCOLL/CStringList::FindIndex
- AFXCOLL/CStringList::GetAt
- AFXCOLL/CStringList::GetCount
- AFXCOLL/CStringList::GetHead
- AFXCOLL/CStringList::GetHeadPosition
- AFXCOLL/CStringList::GetNext
- AFXCOLL/CStringList::GetPrev
- AFXCOLL/CStringList::GetSize
- AFXCOLL/CStringList::GetTail
- AFXCOLL/CStringList::GetTailPosition
- AFXCOLL/CStringList::InsertAfter
- AFXCOLL/CStringList::InsertBefore
- AFXCOLL/CStringList::IsEmpty
- AFXCOLL/CStringList::RemoveAll
- AFXCOLL/CStringList::RemoveAt
- AFXCOLL/CStringList::RemoveHead
- AFXCOLL/CStringList::RemoveTail
- AFXCOLL/CStringList::SetAt
helpviewer_keywords:
- CStringList [MFC], CStringList
- CStringList [MFC], AddHead
- CStringList [MFC], AddTail
- CStringList [MFC], Find
- CStringList [MFC], FindIndex
- CStringList [MFC], GetAt
- CStringList [MFC], GetCount
- CStringList [MFC], GetHead
- CStringList [MFC], GetHeadPosition
- CStringList [MFC], GetNext
- CStringList [MFC], GetPrev
- CStringList [MFC], GetSize
- CStringList [MFC], GetTail
- CStringList [MFC], GetTailPosition
- CStringList [MFC], InsertAfter
- CStringList [MFC], InsertBefore
- CStringList [MFC], IsEmpty
- CStringList [MFC], RemoveAll
- CStringList [MFC], RemoveAt
- CStringList [MFC], RemoveHead
- CStringList [MFC], RemoveTail
- CStringList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: 9eb7a713fc02cd3e51135d1985a41688d4c885d9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447551"
---
# <a name="cstringlist-class"></a>CStringList, classe

Prend en charge des listes d'objets `CString` .

## <a name="syntax"></a>Syntaxe

```
class CStringList : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CStringList` sont similaires aux fonctions membres de la classe [CObList](../../mfc/reference/coblist-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObList` pour connaître les spécificités des fonctions membres. Chaque fois que vous voyez un pointeur `CObject` comme valeur de retour, substituez un `CString` (pas un pointeur `CString`). Chaque fois que vous voyez un pointeur `CObject` comme paramètre de fonction, substituez une `LPCTSTR`.

`CObject*& CObList::GetHead() const;`

par exemple, se traduit par

`CString& CStringList::GetHead() const;`

and

`POSITION AddHead( CObject* <newElement> );`

se traduit par

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CStringList :: CStringList](../../mfc/reference/coblist-class.md#coblist)|Construit une liste vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CStringList :: AddHead](../../mfc/reference/coblist-class.md#addhead)|Ajoute un élément (ou tous les éléments d’une autre liste) au début de la liste (crée un nouvel en-tête).|
|[CStringList :: AddTail](../../mfc/reference/coblist-class.md#addtail)|Ajoute un élément (ou tous les éléments d’une autre liste) à la fin de la liste (crée une nouvelle fin).|
|[CStringList :: find](../../mfc/reference/coblist-class.md#find)|Obtient la position d’un élément spécifié par la valeur de pointeur.|
|[CStringList :: FindIndex](../../mfc/reference/coblist-class.md#findindex)|Obtient la position d’un élément spécifié par un index de base zéro.|
|[CStringList :: GetAt](../../mfc/reference/coblist-class.md#getat)|Obtient l’élément à une position donnée.|
|[CStringList :: GetCount](../../mfc/reference/coblist-class.md#getcount)|Retourne le nombre d’éléments de cette liste.|
|[CStringList :: GetHead](../../mfc/reference/coblist-class.md#gethead)|Retourne l’élément head de la liste (ne peut pas être vide).|
|[CStringList :: GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Retourne la position de l’élément head de la liste.|
|[CStringList :: GetNext](../../mfc/reference/coblist-class.md#getnext)|Obtient l’élément suivant pour l’itération.|
|[CStringList :: GetPrev](../../mfc/reference/coblist-class.md#getprev)|Obtient l’élément précédent pour l’itération.|
|[CStringList :: est à obtenir](../../mfc/reference/coblist-class.md#getsize)|Retourne le nombre d’éléments de cette liste.|
|[CStringList :: GetTail](../../mfc/reference/coblist-class.md#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|
|[CStringList :: GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Retourne la position de l’élément de fin de la liste.|
|[CStringList :: InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Insère un nouvel élément après une position donnée.|
|[CStringList :: InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Insère un nouvel élément avant une position donnée.|
|[CStringList :: IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Teste la condition de liste vide (aucun élément).|
|[CStringList :: RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Supprime tous les éléments de cette liste.|
|[CStringList :: RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Supprime un élément de cette liste, spécifié par position.|
|[CStringList :: RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Supprime l’élément du début de la liste.|
|[CStringList :: RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Supprime l’élément de la fin de la liste.|
|[CStringList :: SetAt](../../mfc/reference/coblist-class.md#setat)|Définit l’élément à une position donnée.|

## <a name="remarks"></a>Notes

Toutes les comparaisons sont effectuées par valeur, ce qui signifie que les caractères de la chaîne sont comparés à la place des adresses des chaînes.

`CStringList` incorpore la macro IMPLEMENT_SERIAL pour prendre en charge la sérialisation et le vidage de ses éléments. Si une liste d’objets `CString` est stockée dans une archive, soit avec un opérateur d’insertion surchargé, soit avec la fonction membre `Serialize`, chaque élément `CString` est sérialisé à son tour.

Si vous avez besoin d’un vidage d’éléments `CString` individuels, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Pour plus d’informations sur l’utilisation de `CStringList`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
