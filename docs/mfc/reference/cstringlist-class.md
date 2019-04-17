---
title: CStringList, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 08e481f010be688fb0b9c219caa1954c9960846f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767273"
---
# <a name="cstringlist-class"></a>CStringList, classe

Prend en charge des listes d'objets `CString` .

## <a name="syntax"></a>Syntaxe

```
class CStringList : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CStringList` sont similaires aux fonctions membres de classe [CObList](../../mfc/reference/coblist-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObList` pour connaître les spécificités des fonctions membres. Partout où vous voyez un `CObject` pointeur en tant que valeur de retour, remplacez un `CString` (pas un `CString` pointeur). Partout où vous voyez un `CObject` pointeur en tant que paramètre de fonction, remplacez un `LPCTSTR`.

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
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|Obtient la position d’un élément spécifié par la valeur de pointeur.|
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|Obtient la position d’un élément spécifié par un index de base zéro.|
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|Obtient l’élément à une position donnée.|
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|Retourne le nombre d’éléments dans cette liste.|
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Retourne l’élément head de la liste (ne peut pas être vide).|
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Retourne la position de l’élément head de la liste.|
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|Obtient l’élément suivant pour une itération.|
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Obtient l’élément précédent pour une itération.|
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|Retourne le nombre d’éléments dans cette liste.|
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Retourne la position de l’élément de fin de la liste.|
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Insère un nouvel élément après une position donnée.|
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Insère un nouvel élément avant une position donnée.|
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Vérifie si la condition de liste vide (aucun élément).|
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Supprime tous les éléments de cette liste.|
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Supprime un élément de cette liste, spécifiée par position.|
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Supprime l’élément de la tête de la liste.|
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Supprime l’élément à partir de la fin de la liste.|
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|Définit l’élément à une position donnée.|

## <a name="remarks"></a>Notes

Toutes les comparaisons sont effectuées par valeur, ce qui signifie que les caractères dans la chaîne sont comparés au lieu des adresses des chaînes.

`CStringList` incorpore la macro IMPLEMENT_SERIAL pour prendre en charge la sérialisation et le vidage de ses éléments. Si une liste de `CString` objets est stocké dans une archive, avec un opérateur d’insertion surchargé ou avec le `Serialize` fonction membre, chaque `CString` élément est sérialisé à son tour.

Si vous avez besoin d’un dump de l’individu `CString` éléments, vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.

Pour plus d’informations sur l’utilisation de `CStringList`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcoll.h

## <a name="see-also"></a>Voir aussi

[Exemple MFC COLLECT](../../overview/visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
