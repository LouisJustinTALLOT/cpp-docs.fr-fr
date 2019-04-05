---
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
ms.openlocfilehash: 383222e4892bccc653f010ce4939bca23f2adc93
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780949"
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
|[CList::CList](#clist)|Construit une liste ordonnée vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CList::AddHead](#addhead)|Ajoute un élément (ou tous les éléments dans une autre liste) au début de la liste (fait une nouvelle tête).|
|[CList::AddTail](#addtail)|Ajoute un élément (ou tous les éléments dans une autre liste) à la fin de la liste (fait une nouvelle fin).|
|[CList::Find](#find)|Obtient la position d’un élément spécifié par la valeur de pointeur.|
|[CList::FindIndex](#findindex)|Obtient la position d’un élément spécifié par un index de base zéro.|
|[CList::GetAt](#getat)|Obtient l’élément à une position donnée.|
|[CList::GetCount](#getcount)|Retourne le nombre d’éléments dans cette liste.|
|[CList::GetHead](#gethead)|Retourne l’élément head de la liste (ne peut pas être vide).|
|[CList::GetHeadPosition](#getheadposition)|Retourne la position de l’élément head de la liste.|
|[CList::GetNext](#getnext)|Obtient l’élément suivant pour une itération.|
|[CList::GetPrev](#getprev)|Obtient l’élément précédent pour une itération.|
|[CList::GetSize](#getsize)|Retourne le nombre d’éléments dans cette liste.|
|[CList::GetTail](#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|
|[CList::GetTailPosition](#gettailposition)|Retourne la position de l’élément de fin de la liste.|
|[CList::InsertAfter](#insertafter)|Insère un nouvel élément après une position donnée.|
|[CList::InsertBefore](#insertbefore)|Insère un nouvel élément avant une position donnée.|
|[CList::IsEmpty](#isempty)|Vérifie si la condition de liste vide (aucun élément).|
|[CList::RemoveAll](#removeall)|Supprime tous les éléments de cette liste.|
|[CList::RemoveAt](#removeat)|Supprime un élément de cette liste, spécifiée par position.|
|[CList::RemoveHead](#removehead)|Supprime l’élément de la tête de la liste.|
|[CList::RemoveTail](#removetail)|Supprime l’élément à partir de la fin de la liste.|
|[CList::SetAt](#setat)|Définit l’élément à une position donnée.|

#### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Type d’objet stocké dans la liste.

*ARG_TYPE*<br/>
Type utilisé pour référencer les objets stockés dans la liste. Peut être une référence.

## <a name="remarks"></a>Notes

`CList` listes se comportent comme les listes à chaînage double.

Une variable de type POSITION est une clé pour la liste. Vous pouvez utiliser une variable POSITION en tant qu’itérateur pour parcourir une liste de façon séquentielle et en tant qu’un signet à un espace réservé. Une position n’est pas identique à un index, toutefois.

Insertion d’éléments est très rapide à la tête de liste, à la fin et à une POSITION connue. Une recherche séquentielle est nécessaire pour rechercher un élément par valeur ou index. Cette recherche peut être lente si la liste est longue.

Si vous avez besoin de vider des éléments individuels dans la liste, vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.

Certaines fonctions de membre de cet appel de la classe d’assistance globales des fonctions qui doivent être personnalisées pour la plupart des utilisations de la `CList` classe. Consultez [Assistants de classe de Collection](../../mfc/reference/collection-class-helpers.md) dans la section « Macros et objet Globals ».

Pour plus d’informations sur l’utilisation de `CList`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtempl.h

##  <a name="addhead"></a>  CList::AddHead

Ajoute un nouvel élément ou une liste d’éléments au début de cette liste.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*newElement*<br/>
Le nouvel élément.

*pNewList*<br/>
Un pointeur vers une autre `CList` liste. Les éléments dans *pNewList* sera ajouté à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version retourne la valeur de la POSITION de l’élément nouvellement inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

##  <a name="addtail"></a>  CList::AddTail

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
Un pointeur vers une autre `CList` liste. Les éléments dans *pNewList* sera ajouté à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version retourne la valeur de la POSITION de l’élément nouvellement inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

##  <a name="clist"></a>  CList::CList

Construit une liste ordonnée vide.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
La granularité d’allocation de mémoire pour l’extension de la liste.

### <a name="remarks"></a>Notes

Que la liste augmente, la mémoire est allouée en unités de *nBlockSize* entrées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

##  <a name="find"></a>  CList::Find

Recherche dans la liste après l’autre pour rechercher le premier élément correspondant spécifié *searchValue*.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*searchValue*<br/>
La valeur à rechercher dans la liste.

*startAfter*<br/>
Position de départ pour la recherche. Si aucune valeur n’est spécifiée, la recherche commence par l’élément head.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si l’objet est introuvable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

##  <a name="findindex"></a>  CList::FindIndex

Utilise la valeur de *nIndex* en tant qu’index dans la liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro de l’élément de liste doit être recherché.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si *nIndex* est négatif ou trop grande.

### <a name="remarks"></a>Notes

Il démarre une analyse séquentielle de la tête de la liste, l’arrêt sur la *n*-ième élément.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

##  <a name="getat"></a>  CList::GetAt

Obtient l’élément de liste à une position donnée.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’objet dans la liste.

*position*<br/>
Position dans la liste de l’élément à obtenir.

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour de `GetHead`.

### <a name="remarks"></a>Notes

`GetAt` Retourne l’élément (ou une référence à l’élément) associée à une position donnée. Il n’est pas identique à un index, et vous ne peut pas fonctionner sur une valeur POSITION vous-même. Une variable de type POSITION est une clé pour la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CList::GetHeadPosition](#getheadposition).

##  <a name="getcount"></a>  CList::GetCount

Obtient le nombre d’éléments dans cette liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur entière qui contient le nombre d’éléments.

### <a name="remarks"></a>Notes

L’appel de cette méthode génère le même résultat que la [CList::GetSize](#getsize) (méthode).

### <a name="example"></a>Exemple

  Consultez l’exemple de [CList::RemoveHead](#removehead).

##  <a name="gethead"></a>  CList::GetHead

Obtient l’élément head (ou une référence à l’élément head) de cette liste.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’objet dans la liste.

### <a name="return-value"></a>Valeur de retour

Si la liste est **const**, `GetHead` retourne une copie de l’élément au début de la liste. Cela permet à la fonction être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège la liste de toute modification.

Si la liste n’est pas **const**, `GetHead` retourne une référence à l’élément au début de la liste. Cela permet la fonction à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetHead`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

##  <a name="getheadposition"></a>  CList::GetHeadPosition

Obtient la position de l’élément head de cette liste.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

##  <a name="getnext"></a>  CList::GetNext

Obtient l’élément de liste identifié par *rPosition*, puis définit *rPosition* à la valeur de la POSITION de l’entrée suivante dans la liste.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments dans la liste.

*rPosition*<br/>
Une référence à une valeur POSITION retournée par une précédente `GetNext`, [GetHeadPosition](#getheadposition), ou un autre appel de fonction membre.

### <a name="return-value"></a>Valeur de retour

Si la liste est **const**, `GetNext` retourne une copie d’un élément de la liste. Cela permet à la fonction être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège la liste de toute modification.

Si la liste n’est pas **const**, `GetNext` retourne une référence à un élément de la liste. Cela permet la fonction à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetNext` dans une boucle d’itération en avant si vous établissez la position initiale avec un appel à `GetHeadPosition` ou `Find`.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

Si l’élément récupéré est le dernier dans la liste, puis la nouvelle valeur de `rPosition` est définie sur NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

##  <a name="getprev"></a>  CList::GetPrev

Obtient l’élément de liste identifié par `rPosition`, puis définit `rPosition` à la valeur de la POSITION de l’entrée précédente dans la liste.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments dans la liste.

*rPosition*<br/>
Une référence à une valeur POSITION retournée par une précédente `GetPrev` ou un autre appel de fonction membre.

### <a name="return-value"></a>Valeur de retour

Si la liste est **const**, `GetPrev` retourne une copie de l’élément au début de la liste. Cela permet à la fonction être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège la liste de toute modification.

Si la liste n’est pas **const**, `GetPrev` retourne une référence à un élément de la liste. Cela permet la fonction à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetPrev` dans une boucle d’itération inverse si vous établissez la position initiale avec un appel à `GetTailPosition` ou `Find`.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

Si l’élément récupéré est le premier dans la liste, puis la nouvelle valeur de *rPosition* est définie sur NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

##  <a name="getsize"></a>  CList::GetSize

Retourne le nombre d’éléments de liste.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments de la liste.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans la liste.  L’appel de cette méthode génère le même résultat que la [CList::GetCount](#getcount) (méthode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

##  <a name="gettail"></a>  CList::GetTail

Obtient le `CObject` pointeur qui représente l’élément de fin de cette liste.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type d’éléments dans la liste.

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour de [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetTail`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

##  <a name="gettailposition"></a>  CList::GetTailPosition

Obtient la position de l’élément de fin de cette liste. NULL si la liste est vide.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

##  <a name="insertafter"></a>  CList::InsertAfter

Ajoute un élément à cette liste après l’élément à la position spécifiée.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Une valeur POSITION retournée par une précédente `GetNext`, `GetPrev`, ou `Find` appel de fonction membre.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste.

*newElement*<br/>
Élément à ajouter à cette liste.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’extraction d’un élément itération ou une liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

##  <a name="insertbefore"></a>  CList::InsertBefore

Ajoute un élément à cette liste avant l’élément à la position spécifiée.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Une valeur POSITION retournée par une précédente `GetNext`, `GetPrev`, ou `Find` appel de fonction membre.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*newElement*<br/>
Élément à ajouter à cette liste.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’extraction d’un élément itération ou une liste.

### <a name="remarks"></a>Notes

Si *position* est NULL, l’élément est inséré au début de la liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

##  <a name="isempty"></a>  CList::IsEmpty

Indique si cette liste ne contient aucun élément.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si cette liste est vide. sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

##  <a name="removeall"></a>  CList::RemoveAll

Supprime tous les éléments de cette liste et libère la mémoire associée.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Aucune erreur n’est générée si la liste est déjà vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

##  <a name="removeat"></a>  CList::RemoveAt

Supprime l’élément spécifié à partir de cette liste.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
La position de l’élément à supprimer de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

##  <a name="removehead"></a>  CList::RemoveHead

Supprime l’élément de la tête de la liste et retourne un pointeur vers elle.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type d’éléments dans la liste.

### <a name="return-value"></a>Valeur de retour

L’élément précédemment au début de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveHead`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

##  <a name="removetail"></a>  CList::RemoveTail

Supprime l’élément de la fin de la liste et retourne un pointeur vers elle.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type d’éléments dans la liste.

### <a name="return-value"></a>Valeur de retour

L’élément qui était à la fin de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveTail`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

##  <a name="setat"></a>  CList::SetAt

Une variable de type POSITION est une clé pour la liste.

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
La POSITION de l’élément à définir.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type de l’élément de liste (peut être une référence).

*newElement*<br/>
L’élément à ajouter à la liste.

### <a name="remarks"></a>Notes

Il n’est pas identique à un index, et vous ne peut pas fonctionner sur une valeur POSITION vous-même. `SetAt` écrit l’élément à la position spécifiée dans la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC COLLECT](../../overview/visual-cpp-samples.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMap (classe)](../../mfc/reference/cmap-class.md)<br/>
[CArray (classe)](../../mfc/reference/carray-class.md)
