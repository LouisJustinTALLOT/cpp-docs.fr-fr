---
description: 'En savoir plus sur : CList Class'
title: CList (classe)
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
ms.openlocfilehash: e216bda53c37c325ffb8aeb943d4cefb223ac1d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236683"
---
# <a name="clist-class"></a>CList (classe)

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
|[CList :: CList](#clist)|Construit une liste triée vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CList :: AddHead](#addhead)|Ajoute un élément (ou tous les éléments d’une autre liste) au début de la liste (crée un nouvel en-tête).|
|[CList :: AddTail](#addtail)|Ajoute un élément (ou tous les éléments d’une autre liste) à la fin de la liste (crée une nouvelle fin).|
|[CList :: find](#find)|Obtient la position d’un élément spécifié par la valeur de pointeur.|
|[CList :: FindIndex](#findindex)|Obtient la position d’un élément spécifié par un index de base zéro.|
|[CList :: GetAt](#getat)|Obtient l’élément à une position donnée.|
|[CList :: GetCount](#getcount)|Retourne le nombre d’éléments de cette liste.|
|[CList :: GetHead](#gethead)|Retourne l’élément head de la liste (ne peut pas être vide).|
|[CList :: GetHeadPosition](#getheadposition)|Retourne la position de l’élément head de la liste.|
|[CList :: GetNext](#getnext)|Obtient l’élément suivant pour l’itération.|
|[CList :: GetPrev](#getprev)|Obtient l’élément précédent pour l’itération.|
|[CList :: Deis](#getsize)|Retourne le nombre d’éléments de cette liste.|
|[CList :: GetTail](#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|
|[CList :: GetTailPosition](#gettailposition)|Retourne la position de l’élément de fin de la liste.|
|[CList :: InsertAfter](#insertafter)|Insère un nouvel élément après une position donnée.|
|[CList::InsertBefore](#insertbefore)|Insère un nouvel élément avant une position donnée.|
|[CList :: IsEmpty](#isempty)|Teste la condition de liste vide (aucun élément).|
|[CList :: RemoveAll](#removeall)|Supprime tous les éléments de cette liste.|
|[CList :: RemoveAt](#removeat)|Supprime un élément de cette liste, spécifié par position.|
|[CList :: RemoveHead](#removehead)|Supprime l’élément du début de la liste.|
|[CList :: RemoveTail](#removetail)|Supprime l’élément de la fin de la liste.|
|[CList :: SetAt](#setat)|Définit l’élément à une position donnée.|

#### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Type d’objet stocké dans la liste.

*ARG_TYPE*<br/>
Type utilisé pour référencer des objets stockés dans la liste. Peut être une référence.

## <a name="remarks"></a>Notes

`CList` les listes se comportent comme des listes doublement liées.

Une variable de type POSITION est une clé pour la liste. Vous pouvez utiliser une variable de POSITION comme itérateur pour parcourir une liste de façon séquentielle et comme signet pour stocker un emplacement. Toutefois, une position n’est pas identique à un index.

L’insertion d’élément est très rapide à l’en-tête de liste, à la fin et à une POSITION connue. Une recherche séquentielle est nécessaire pour rechercher un élément par valeur ou par index. Cette recherche peut être lente si la liste est longue.

Si vous avez besoin d’un vidage d’éléments individuels dans la liste, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Certaines fonctions membres de cette classe appellent des fonctions d’assistance globales qui doivent être personnalisées pour la plupart des utilisations de la `CList` classe. Pour plus d’informations, consultez la section « macros et globales » de [classe de collection](../../mfc/reference/collection-class-helpers.md) .

Pour plus d’informations sur l’utilisation de `CList` , consultez l’article [Collections](../../mfc/collections.md).

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a> CList :: AddHead

Ajoute un nouvel élément ou une liste d’éléments au début de cette liste.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*newElement*<br/>
Nouvel élément.

*pNewList*<br/>
Pointeur vers une autre `CList` liste. Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur renvoyée

La première version retourne la valeur de POSITION de l’élément qui vient d’être inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a> CList :: AddTail

Ajoute un nouvel élément ou une liste d’éléments à la fin de cette liste.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*newElement*<br/>
Élément à ajouter à cette liste.

*pNewList*<br/>
Pointeur vers une autre `CList` liste. Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur renvoyée

La première version retourne la valeur de POSITION de l’élément qui vient d’être inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a> CList :: CList

Construit une liste triée vide.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Granularité d’allocation de mémoire pour étendre la liste.

### <a name="remarks"></a>Notes

À mesure que la liste croît, la mémoire est allouée en unités d’entrées *nBlockSize* .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a> CList :: find

Recherche séquentiellement la liste pour trouver le premier élément correspondant au *searchValue* spécifié.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*searchValue*<br/>
Valeur à rechercher dans la liste.

*startAfter*<br/>
Position de départ de la recherche. Si aucune valeur n’est spécifiée, la recherche commence par l’élément head.

### <a name="return-value"></a>Valeur renvoyée

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si l’objet est introuvable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a> CList :: FindIndex

Utilise la valeur de *nIndex* en tant qu’index dans la liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro de l’élément de liste à trouver.

### <a name="return-value"></a>Valeur renvoyée

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si *nIndex* est négatif ou trop grand.

### <a name="remarks"></a>Notes

Il démarre une analyse séquentielle à partir du début de la liste, en arrêtant sur le *n* ième élément.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a> CList :: GetAt

Obtient l’élément de liste à une position donnée.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’objet dans la liste.

*position*<br/>
Position dans la liste de l’élément à récupérer.

### <a name="return-value"></a>Valeur renvoyée

Consultez la description de la valeur de retour pour `GetHead` .

### <a name="remarks"></a>Notes

`GetAt` retourne l’élément (ou une référence à l’élément) associé à une position donnée. Ce n’est pas le même qu’un index, et vous ne pouvez pas utiliser une valeur POSITION vous-même. Une variable de type POSITION est une clé pour la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CList :: GetHeadPosition](#getheadposition).

## <a name="clistgetcount"></a><a name="getcount"></a> CList :: GetCount

Obtient le nombre d’éléments de cette liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur entière contenant le nombre d’éléments.

### <a name="remarks"></a>Notes

L’appel de cette méthode génère le même résultat que la méthode [CList ::](#getsize) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CList :: RemoveHead](#removehead).

## <a name="clistgethead"></a><a name="gethead"></a> CList :: GetHead

Obtient l’élément Head (ou une référence à l’élément head) de cette liste.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’objet dans la liste.

### <a name="return-value"></a>Valeur renvoyée

Si la liste est **`const`** , `GetHead` retourne une copie de l’élément au début de la liste. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger la liste contre toute modification.

Si la liste n’est pas **`const`** , `GetHead` retourne une référence à l’élément situé à l’en-tête de la liste. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetHead` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a> CList :: GetHeadPosition

Obtient la position de l’élément head de cette liste.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a> CList :: GetNext

Obtient l’élément de liste identifié par *rPosition*, puis affecte à *rPosition* la valeur de position de l’entrée suivante dans la liste.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments de la liste.

*rPosition*<br/>
Référence à une valeur de POSITION retournée par un `GetNext` appel de fonction membre précédent, [GetHeadPosition](#getheadposition)ou autre.

### <a name="return-value"></a>Valeur renvoyée

Si la liste est **`const`** , `GetNext` retourne une copie d’un élément de la liste. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger la liste contre toute modification.

Si la liste n’est pas **`const`** , `GetNext` retourne une référence à un élément de la liste. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetNext` dans une boucle d’itération anticipée si vous établissez la position initiale avec un appel à `GetHeadPosition` ou `Find` .

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Si l’élément récupéré est le dernier de la liste, la nouvelle valeur de `rPosition` est définie sur null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a> CList :: GetPrev

Obtient l’élément de liste identifié par `rPosition` , puis définit `rPosition` à la valeur de position de l’entrée précédente dans la liste.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments de la liste.

*rPosition*<br/>
Référence à une valeur de POSITION retournée par un `GetPrev` appel de fonction membre ou précédent.

### <a name="return-value"></a>Valeur renvoyée

Si la liste est **`const`** , `GetPrev` retourne une copie de l’élément au début de la liste. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger la liste contre toute modification.

Si la liste n’est pas **`const`** , `GetPrev` retourne une référence à un élément de la liste. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetPrev` dans une boucle d’itération inverse si vous établissez la position initiale avec un appel à `GetTailPosition` ou `Find` .

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Si l’élément récupéré est le premier de la liste, la nouvelle valeur de *rPosition* est définie sur null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a> CList :: Deis

Retourne le nombre d’éléments de liste.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d'éléments dans la liste.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans la liste.  L’appel de cette méthode génère le même résultat que la méthode [CList :: GetCount](#getcount) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a> CList :: GetTail

Obtient le `CObject` pointeur qui représente l’élément de fin de cette liste.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments de la liste.

### <a name="return-value"></a>Valeur renvoyée

Consultez la description de la valeur de retour pour [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetTail` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a> CList :: GetTailPosition

Obtient la position de l’élément de fin de cette liste ; NULL si la liste est vide.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a> CList :: InsertAfter

Ajoute un élément à cette liste après l’élément à la position spécifiée.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Valeur de POSITION retournée par un `GetNext` `GetPrev` appel de fonction membre, ou précédent `Find` .

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste.

*newElement*<br/>
Élément à ajouter à cette liste.

### <a name="return-value"></a>Valeur renvoyée

Une valeur POSITION qui peut être utilisé pour l’itération ou l’extraction d’un élément de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a> CList :: InsertBefore

Ajoute un élément à cette liste avant l’élément à la position spécifiée.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Valeur de POSITION retournée par un `GetNext` `GetPrev` appel de fonction membre, ou précédent `Find` .

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*newElement*<br/>
Élément à ajouter à cette liste.

### <a name="return-value"></a>Valeur renvoyée

Une valeur POSITION qui peut être utilisé pour l’itération ou l’extraction d’un élément de liste.

### <a name="remarks"></a>Notes

Si *position* est null, l’élément est inséré au début de la liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a> CList :: IsEmpty

Indique si cette liste ne contient aucun élément.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si cette liste est vide ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a> CList :: RemoveAll

Supprime tous les éléments de cette liste et libère la mémoire associée.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Aucune erreur n’est générée si la liste est déjà vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a> CList :: RemoveAt

Supprime l’élément spécifié de cette liste.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Position de l’élément à supprimer de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a> CList :: RemoveHead

Supprime l’élément de l’en-tête de la liste et retourne un pointeur vers celui-ci.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments de la liste.

### <a name="return-value"></a>Valeur renvoyée

Élément précédemment situé à l’en-tête de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveHead` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a> CList :: RemoveTail

Supprime l’élément de la fin de la liste et retourne un pointeur vers celui-ci.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments de la liste.

### <a name="return-value"></a>Valeur renvoyée

Élément qui était à la fin de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveTail` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a> CList :: SetAt

Une variable de type POSITION est une clé pour la liste.

```cpp
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
POSITION de l’élément à définir.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*newElement*<br/>
Élément à ajouter à la liste.

### <a name="remarks"></a>Notes

Ce n’est pas le même qu’un index, et vous ne pouvez pas utiliser une valeur POSITION vous-même. `SetAt` écrit l’élément à la position spécifiée dans la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMap, classe](../../mfc/reference/cmap-class.md)<br/>
[CArray (classe)](../../mfc/reference/carray-class.md)
