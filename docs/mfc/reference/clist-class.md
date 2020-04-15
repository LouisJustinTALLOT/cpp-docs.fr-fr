---
title: CList, classe
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 253cf12033af497115ad600e457630ae834cc69c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372246"
---
# <a name="clist-class"></a>CList, classe

Prend en charge les listes ordonnées d'objets non uniques accessibles séquentiellement ou par valeur.

## <a name="syntax"></a>Syntaxe

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Liste::CList](#clist)|Construit une liste de commande vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CList::AddHead](#addhead)|Ajoute un élément (ou tous les éléments d’une autre liste) à la tête de la liste (fait une nouvelle tête).|
|[CList::AddTail](#addtail)|Ajoute un élément (ou tous les éléments d’une autre liste) à la queue de la liste (fait une nouvelle queue).|
|[CList::Trouver](#find)|Obtient la position d’un élément spécifié par la valeur de pointeur.|
|[CList::FindIndex](#findindex)|Obtient la position d’un élément spécifié par un index à base nulle.|
|[Liste::GetAt](#getat)|Obtient l’élément à une position donnée.|
|[Liste::GetCount](#getcount)|Retourne le nombre d’éléments dans cette liste.|
|[CList::GetHead](#gethead)|Retourne l’élément tête de la liste (ne peut pas être vide).|
|[CList::GetHeadPosition](#getheadposition)|Retourne la position de l’élément tête de la liste.|
|[CList::GetNext](#getnext)|Obtient le prochain élément pour itérer.|
|[CList::GetPrev](#getprev)|Obtient l’élément précédent pour itérer.|
|[CList::GetSize](#getsize)|Retourne le nombre d’éléments dans cette liste.|
|[CList::GetTail](#gettail)|Retourne l’élément de queue de la liste (ne peut pas être vide).|
|[CList::GetTailPosition](#gettailposition)|Retourne la position de l’élément queue de la liste.|
|[CList::InsertAfter](#insertafter)|Insère un nouvel élément après une position donnée.|
|[CList::InsertBefore](#insertbefore)|Insère un nouvel élément avant une position donnée.|
|[CList::IsEmpty](#isempty)|Tests pour l’état de liste vide (pas d’éléments).|
|[CList::RemoveAll](#removeall)|Supprime tous les éléments de cette liste.|
|[CList::RemoveAt](#removeat)|Supprime un élément de cette liste, spécifié par position.|
|[CList::RemoveHead](#removehead)|Supprime l’élément de la tête de liste.|
|[CList::RemoveTail](#removetail)|Supprime l’élément de la queue de la liste.|
|[CList::SetAt](#setat)|Définit l’élément à une position donnée.|

#### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Type d’objet stocké dans la liste.

*ARG_TYPE*<br/>
Type utilisé pour référencer les objets stockés dans la liste. Peut être une référence.

## <a name="remarks"></a>Notes

`CList`les listes se comportent comme des listes doublement liées.

Une variable de type POSITION est une clé pour la liste. Vous pouvez utiliser une variable POSITION comme itérateur pour parcourir une liste séquentiellement et comme signet pour tenir une place. Une position n’est cependant pas la même qu’un indice.

L’insertion d’éléments est très rapide à la tête de liste, à la queue, et à un POSITION connu. Une recherche séquentielle est nécessaire pour rechercher un élément par valeur ou index. Cette recherche peut être lente si la liste est longue.

Si vous avez besoin d’un dépotoir d’éléments individuels dans la liste, vous devez définir la profondeur du contexte de décharge à 1 ou plus.

Certaines fonctions membres de cette classe appellent fonctions d’aide globale `CList` qui doivent être personnalisées pour la plupart des utilisations de la classe. Voir [les aides de classe de collection](../../mfc/reference/collection-class-helpers.md) dans la section « Macros et Globals ».

Pour plus d’informations sur l’utilisation `CList`, voir l’article [Collections](../../mfc/collections.md).

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CList::AddHead

Ajoute un nouvel élément ou une liste d’éléments à la tête de cette liste.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*nouvel Element*<br/>
Nouvel élément.

*pNewList (en)*<br/>
Un pointeur `CList` vers une autre liste. Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version renvoie la valeur POSITION de l’élément nouvellement inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList::AddTail

Ajoute un nouvel élément ou une liste d’éléments à la queue de cette liste.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*nouvel Element*<br/>
Élément à ajouter à cette liste.

*pNewList (en)*<br/>
Un pointeur `CList` vers une autre liste. Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version renvoie la valeur POSITION de l’élément nouvellement inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>Liste::CList

Construit une liste de commande vide.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
La granularité de l’allocation de mémoire pour l’extension de la liste.

### <a name="remarks"></a>Notes

Au fur et à mesure que la liste s’allonge, la mémoire est attribuée dans les unités d’entrées *nBlockSize.*

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>CList::Trouver

Recherche la liste séquentiellement pour trouver le premier élément correspondant à la *recherche spécifiéeValue*.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*searchValue (en)*<br/>
La valeur à trouver dans la liste.

*startAprès*<br/>
La position de départ pour la recherche. Si aucune valeur n’est spécifiée, la recherche commence par l’élément de tête.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si l’objet n’est pas trouvé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>CList::FindIndex

Utilise la valeur de *nIndex* comme un indice dans la liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’indice zéro de l’élément de liste à trouver.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si *nIndex* est négatif ou trop grand.

### <a name="remarks"></a>Notes

Il commence un scan séquentiel de la tête de la liste, s’arrêtant sur *l’élément n*e.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>Liste::GetAt

Obtient l’élément de liste à une position donnée.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’objet dans la liste.

*position*<br/>
La position dans la liste de l’élément à obtenir.

### <a name="return-value"></a>Valeur de retour

Voir la description `GetHead`de la valeur de retour pour .

### <a name="remarks"></a>Notes

`GetAt`renvoie l’élément (ou une référence à l’élément) associé à une position donnée. Ce n’est pas la même chose qu’un index, et vous ne pouvez pas fonctionner sur une valeur POSITION vous-même. Une variable de type POSITION est une clé pour la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CList:GetHeadPosition](#getheadposition).

## <a name="clistgetcount"></a><a name="getcount"></a>Liste::GetCount

Obtient le nombre d’éléments dans cette liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur d’intégrant contenant le nombre d’éléments.

### <a name="remarks"></a>Notes

L’appel de cette méthode générera le même résultat que la [méthode CList:GetSize.](#getsize)

### <a name="example"></a>Exemple

  Voir l’exemple pour [CList:RemoveHead](#removehead).

## <a name="clistgethead"></a><a name="gethead"></a>CList::GetHead

Obtient l’élément de tête (ou une référence à l’élément de tête) de cette liste.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’objet dans la liste.

### <a name="return-value"></a>Valeur de retour

Si la liste est `GetHead` **const**, renvoie une copie de l’élément à la tête de la liste. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège la liste contre la modification.

Si la liste **n’est**pas const , `GetHead` renvoie une référence à l’élément en tête de liste. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `GetHead`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList::GetHeadPosition

Obtient la position de l’élément de tête de cette liste.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList::GetNext

Obtient l’élément de liste identifié par *rPosition*, puis définit *rPosition* à la valeur POSITION de la prochaine entrée dans la liste.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments de la liste.

*rPosition*<br/>
Une référence à une valeur `GetNext`POSITION retournée par un précédent , [GetHeadPosition](#getheadposition), ou un autre appel de fonction de membre.

### <a name="return-value"></a>Valeur de retour

Si la liste est `GetNext` **const**, renvoie une copie d’un élément de la liste. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège la liste contre la modification.

Si la liste **n’est**pas const , `GetNext` renvoie une référence à un élément de la liste. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous pouvez `GetNext` utiliser dans une boucle d’itération vers l’avant si vous établissez la position initiale avec un appel à `GetHeadPosition` ou `Find`.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Si l’élément récupéré est le dernier de la `rPosition` liste, alors la nouvelle valeur est définie à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList::GetPrev

Obtient l’élément `rPosition`de liste `rPosition` identifié par , puis se définit à la valeur POSITION de l’entrée précédente dans la liste.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments de la liste.

*rPosition*<br/>
Une référence à une valeur `GetPrev` POSITION retournée par un appel de fonction de membre précédent ou autre.

### <a name="return-value"></a>Valeur de retour

Si la liste est `GetPrev` **const**, renvoie une copie de l’élément à la tête de la liste. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège la liste contre la modification.

Si la liste **n’est**pas const , `GetPrev` renvoie une référence à un élément de la liste. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous pouvez `GetPrev` utiliser dans une boucle d’itération inversée `GetTailPosition` si `Find`vous établissez la position initiale avec un appel à ou .

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Si l’élément récupéré est le premier de la liste, la nouvelle valeur de *la rPosition* est réglée sur NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>CList::GetSize

Retourne le nombre d’éléments de liste.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments dans la liste.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments de la liste.  L’appel de cette méthode générera le même résultat que la méthode [CList::GetCount.](#getcount)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>CList::GetTail

Obtient `CObject` le pointeur qui représente l’élément de queue de cette liste.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments de la liste.

### <a name="return-value"></a>Valeur de retour

Voir la description de la valeur de retour pour [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `GetTail`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>CList::GetTailPosition

Obtient la position de l’élément de queue de cette liste; NULL si la liste est vide.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList::InsertAfter

Ajoute un élément à cette liste après l’élément à la position spécifiée.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Une valeur POSITION retournée `GetNext` `GetPrev`par `Find` un précédent , , ou appel de fonction de membre.

*ARG_TYPE*<br/>
Paramètre de modèle spécifiant le type de l’élément de liste.

*nouvel Element*<br/>
Élément à ajouter à cette liste.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisé pour l’itération ou l’extraction d’un élément de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList::InsertBefore

Ajoute un élément à cette liste avant l’élément à la position spécifiée.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Une valeur POSITION retournée `GetNext` `GetPrev`par `Find` un précédent , , ou appel de fonction de membre.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*nouvel Element*<br/>
Élément à ajouter à cette liste.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisé pour l’itération ou l’extraction d’un élément de liste.

### <a name="remarks"></a>Notes

Si *la position* est NULL, l’élément est inséré en tête de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList::IsEmpty

Indique si cette liste ne contient aucun élément.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si cette liste est vide; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList::RemoveAll

Supprime tous les éléments de cette liste et libère la mémoire associée.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Aucune erreur n’est générée si la liste est déjà vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CList::RemoveAt

Supprime l’élément spécifié de cette liste.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
La position de l’élément à supprimer de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>CList::RemoveHead

Supprime l’élément de la tête de la liste et y renvoie un pointeur.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments de la liste.

### <a name="return-value"></a>Valeur de retour

L’élément précédemment en tête de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `RemoveHead`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>CList::RemoveTail

Supprime l’élément de la queue de la liste et y renvoie un pointeur.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments de la liste.

### <a name="return-value"></a>Valeur de retour

L’élément qui était à la queue de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `RemoveTail`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList::SetAt

Une variable de type POSITION est une clé pour la liste.

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le POSITION de l’élément à définir.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*nouvel Element*<br/>
L’élément à ajouter à la liste.

### <a name="remarks"></a>Notes

Ce n’est pas la même chose qu’un index, et vous ne pouvez pas fonctionner sur une valeur POSITION vous-même. `SetAt`écrit l’élément à la position spécifiée dans la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMap, classe](../../mfc/reference/cmap-class.md)<br/>
[Classe CArray](../../mfc/reference/carray-class.md)
