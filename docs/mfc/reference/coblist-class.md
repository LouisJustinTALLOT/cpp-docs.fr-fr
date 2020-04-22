---
title: CObList, classe
ms.date: 11/04/2016
f1_keywords:
- CObList
- AFXCOLL/CObList
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
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
ms.openlocfilehash: f24965357e0b71f28ba39b82d045600e7e1a44e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749686"
---
# <a name="coblist-class"></a>CObList, classe

fSupports a ordonné des `CObject` listes de pointeurs non syndiqués accessibles séquentiellement ou par valeur pointeur.

## <a name="syntax"></a>Syntaxe

```
class CObList : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CObList::CObList](#coblist)|Construit une liste `CObject` vide pour les pointeurs.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObList::AddHead](#addhead)|Ajoute un élément (ou tous les éléments d’une autre liste) à la tête de la liste (fait une nouvelle tête).|
|[CObList::AddTail](#addtail)|Ajoute un élément (ou tous les éléments d’une autre liste) à la queue de la liste (fait une nouvelle queue).|
|[CObList::Trouver](#find)|Obtient la position d’un élément spécifié par la valeur de pointeur.|
|[CObList::FindIndex](#findindex)|Obtient la position d’un élément spécifié par un index à base nulle.|
|[CObList::GetAt](#getat)|Obtient l’élément à une position donnée.|
|[CObList::GetCount](#getcount)|Retourne le nombre d’éléments dans cette liste.|
|[CObList::GetHead](#gethead)|Retourne l’élément tête de la liste (ne peut pas être vide).|
|[CObList::GetHeadPosition](#getheadposition)|Retourne la position de l’élément tête de la liste.|
|[CObList:GetNext](#getnext)|Obtient le prochain élément pour itérer.|
|[CObList::GetPrev](#getprev)|Obtient l’élément précédent pour itérer.|
|[CObList::GetSize](#getsize)|Retourne le nombre d’éléments dans cette liste.|
|[CObList::GetTail](#gettail)|Retourne l’élément de queue de la liste (ne peut pas être vide).|
|[CObList::GetTailPosition](#gettailposition)|Retourne la position de l’élément queue de la liste.|
|[CObList::InsertAfter](#insertafter)|Insère un nouvel élément après une position donnée.|
|[CObList::InsertBefore](#insertbefore)|Insère un nouvel élément avant une position donnée.|
|[CObList:IsEmpty](#isempty)|Tests pour l’état de liste vide (pas d’éléments).|
|[CObList::RemoveAll](#removeall)|Supprime tous les éléments de cette liste.|
|[CObList::RemoveAt](#removeat)|Supprime un élément de cette liste, spécifié par position.|
|[CObList::RemoveHead](#removehead)|Supprime l’élément de la tête de liste.|
|[CObList::RemoveTail](#removetail)|Supprime l’élément de la queue de la liste.|
|[CObList::SetAt](#setat)|Définit l’élément à une position donnée.|

## <a name="remarks"></a>Notes

`CObList`les listes se comportent comme des listes doublement liées.

Une variable de type POSITION est une clé pour la liste. Vous pouvez utiliser une variable POSITION à la fois comme itérateur pour parcourir une liste séquentiellement et comme un signet pour tenir une place. Une position n’est cependant pas la même qu’un indice.

L’insertion d’éléments est très rapide à la tête de liste, à la queue, et à un POSITION connu. Une recherche séquentielle est nécessaire pour rechercher un élément par valeur ou index. Cette recherche peut être lente si la liste est longue.

`CObList`intègre la macro IMPLEMENT_SERIAL pour soutenir la sérialisation et le dumping de ses éléments. Si une `CObject` liste de pointeurs est stockée dans une archive, soit `Serialize` avec un `CObject` opérateur d’insertion surchargé ou avec la fonction membre, chaque élément est sérialisé à son tour.

Si vous avez besoin `CObject` d’un dépotoir d’éléments individuels dans la liste, vous devez définir la profondeur du contexte de décharge à 1 ou plus.

Lorsqu’un `CObList` objet est supprimé, ou lorsque ses `CObject` éléments sont supprimés, seuls les pointeurs sont supprimés, et non les objets qu’ils renvoient.

Vous pouvez tirer vos `CObList`propres classes de . Votre nouvelle classe de liste, conçue pour `CObject`tenir des indications sur les objets dérivés , ajoute de nouveaux membres de données et de nouvelles fonctions de membre. Notez que la liste résultante n’est pas `CObject` strictement de type sûr, car il permet l’insertion de n’importe quel pointeur.

> [!NOTE]
> Vous devez utiliser la [macro IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) dans la mise en œuvre de votre classe dérivée si vous avez l’intention de sérialiser la liste.

Pour plus d’informations sur l’utilisation `CObList`, voir l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Spécifications

**En-tête:** afxcoll.h

## <a name="coblistaddhead"></a><a name="addhead"></a>CObList::AddHead

Ajoute un nouvel élément ou une liste d’éléments à la tête de cette liste.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Paramètres

*nouvel Element*<br/>
Le `CObject` pointeur à ajouter à cette liste.

*pNewList (en)*<br/>
Un pointeur `CObList` vers une autre liste. Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version renvoie la valeur POSITION de l’élément nouvellement inséré.

Le tableau suivant montre d’autres `CObList::AddHead`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddHead** <strong>\*</strong> `newElement` **(vide);**<br /><br /> **void AddHead (CPtrList);** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddHead (const CString** `newElement` **&);**<br /><br /> **POSITION AddHead (LPCTSTR);** `newElement` **);**<br /><br /> **void AddHead(CStringList);** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

  Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Les résultats de ce programme sont les suivants :

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

## <a name="coblistaddtail"></a><a name="addtail"></a>CObList::AddTail

Ajoute un nouvel élément ou une liste d’éléments à la queue de cette liste.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Paramètres

*nouvel Element*<br/>
Le `CObject` pointeur à ajouter à cette liste.

*pNewList (en)*<br/>
Un pointeur `CObList` vers une autre liste. Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version renvoie la valeur POSITION de l’élément nouvellement inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

Le tableau suivant montre d’autres `CObList::AddTail`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddTail** <strong>\*</strong> `newElement` **(vide);**<br /><br /> **void AddTail(CPtrList);** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddTail (const CString** `newElement` **&);**<br /><br /> **POSITION AddTail (LPCTSTR);** `newElement` **);**<br /><br /> **void AddTail (CStringList);** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Les résultats de ce programme sont les suivants :

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

## <a name="coblistcoblist"></a><a name="coblist"></a>CObList::CObList

Construit une `CObject` liste de pointeurs vides.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
La granularité de l’allocation de mémoire pour l’extension de la liste.

### <a name="remarks"></a>Notes

Au fur et à mesure que la liste s’allonge, la mémoire est attribuée dans les unités d’entrées *nBlockSize.* Si une allocation de `CMemoryException` mémoire échoue, un est jeté.

Le tableau suivant montre d’autres `CObList::CObList`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **10);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **10);**|

### <a name="example"></a>Exemple

  Voici une liste `CObject`de la `CAge` classe dérivée utilisée dans tous les exemples de collection :

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Voici un exemple `CObList` d’utilisation des constructeurs :

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

## <a name="coblistfind"></a><a name="find"></a>CObList::Trouver

Recherche la liste séquentiellement `CObject` pour trouver `CObject` le premier pointeur correspondant au pointeur spécifié.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Paramètres

*searchValue (en)*<br/>
Le pointeur d’objet à trouver dans cette liste.

*startAprès*<br/>
La position de départ pour la recherche.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si l’objet n’est pas trouvé.

### <a name="remarks"></a>Notes

Notez que les valeurs de pointeur sont comparées, pas le contenu des objets.

Le tableau suivant montre d’autres `CObList::Find`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION Trouver ( vide** <strong>\*</strong> `searchValue` **, POSITION** `startAfter` **- NULL ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION Trouver ( LPCTSTR** `searchValue` **, POSITION** `startAfter` **et NULL ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

## <a name="coblistfindindex"></a><a name="findindex"></a>CObList::FindIndex

Utilise la valeur de *nIndex* comme un indice dans la liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’indice zéro de l’élément de liste à trouver.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si *nIndex* est trop grand. (Le cadre génère une affirmation si *nIndex* est négatif.)

### <a name="remarks"></a>Notes

Il commence un scan séquentiel de la tête de la liste, s’arrêtant sur *l’élément n*e.

Le tableau suivant montre d’autres `CObList::FindIndex`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION FindIndex ( INT_PTR** `nIndex` **) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION FindIndex ( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

## <a name="coblistgetat"></a><a name="getat"></a>CObList::GetAt

Une variable de type POSITION est une clé pour la liste.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Paramètres

*Position*<br/>
Une valeur POSITION retournée `GetHeadPosition` `Find` par un appel de fonction préalable ou membre.

### <a name="return-value"></a>Valeur de retour

Voir la description de la valeur de retour pour [GetHead](#gethead).

### <a name="remarks"></a>Notes

Ce n’est pas la même chose qu’un index, et vous ne pouvez pas fonctionner sur une valeur POSITION vous-même. `GetAt`récupère le `CObject` pointeur associé à une position donnée.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Le tableau suivant montre d’autres `CObList::GetAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* vide& GetAt ( position POSITION** ) *position* **const;**<br /><br /> **vide\*& GetAt (position** *position* **POSITION);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetAt ( POSITION POSITION** *position* **) const;**<br /><br /> **CString& GetAt (position** *position* **POSITION);**|

### <a name="example"></a>Exemple

  Voir l’exemple pour [FindIndex](#findindex).

## <a name="coblistgetcount"></a><a name="getcount"></a>CObList::GetCount

Obtient le nombre d’éléments dans cette liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur d’intégrant contenant le nombre d’éléments.

Le tableau suivant montre d’autres `CObList::GetCount`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount) ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount) ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

## <a name="coblistgethead"></a><a name="gethead"></a>CObList::GetHead

Obtient `CObject` le pointeur qui représente l’élément de tête de cette liste.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Valeur de retour

Si la liste est accessible par `const CObList`un `GetHead` pointeur à un , puis retourne un `CObject` pointeur. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège ainsi la liste contre la modification.

Si la liste est consultée directement `CObList`ou `GetHead` par l’intermédiaire `CObject` d’un pointeur à un , puis retourne une référence à un pointeur. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `GetHead`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant montre d’autres `CObList::GetHead`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* vide& GetHead) ) const; vide\*& GetHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetHead) ) const; CString& GetHead, );**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

L’exemple suivant illustre `GetHead` l’utilisation du côté gauche d’une déclaration d’affectation.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

## <a name="coblistgetheadposition"></a><a name="getheadposition"></a>CObList::GetHeadPosition

Obtient la position de l’élément de tête de cette liste.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si la liste est vide.

Le tableau suivant montre d’autres `CObList::GetHeadPosition`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition( ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

## <a name="coblistgetnext"></a><a name="getnext"></a>CObList:GetNext

Obtient l’élément de liste identifié par *rPosition*, puis définit *rPosition* à la `POSITION` valeur de la prochaine entrée dans la liste.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Une référence à une valeur `GetNext`POSITION `GetHeadPosition`retournée par un précédent , , ou un autre appel de fonction de membre.

### <a name="return-value"></a>Valeur de retour

Voir la description de la valeur de retour pour [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous pouvez `GetNext` utiliser dans une boucle d’itération vers l’avant si vous établissez la position initiale avec un appel à `GetHeadPosition` ou `Find`.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Si l’élément récupéré est le dernier de la liste, alors la nouvelle valeur de *rPosition* est réglée à NULL.

Il est possible d’enlever un élément lors d’une itération. Voir l’exemple pour [RemoveAt](#removeat).

> [!NOTE]
> En date de MFC 8.0 la version const de cette méthode a changé pour revenir `const CObject*` au lieu de `const CObject*&`.  Cette modification a été apportée pour mettre le compilateur en conformité avec la norme C.

Le tableau suivant montre d’autres `CObList::GetNext`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Les résultats de ce programme sont les suivants :

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

## <a name="coblistgetprev"></a><a name="getprev"></a>CObList::GetPrev

Obtient l’élément de liste identifié par *rPosition*, puis définit *rPosition* à la valeur POSITION de l’entrée précédente dans la liste.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Une référence à une valeur `GetPrev` POSITION retournée par un appel de fonction de membre précédent ou autre.

### <a name="return-value"></a>Valeur de retour

Voir la description de la valeur de retour pour [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous pouvez `GetPrev` utiliser dans une boucle d’itération inversée `GetTailPosition` si `Find`vous établissez la position initiale avec un appel à ou .

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Si l’élément récupéré est le premier de la liste, la nouvelle valeur de *la rPosition* est réglée sur NULL.

> [!NOTE]
> En date de MFC 8.0 la version const de cette méthode a changé pour revenir `const CObject*` au lieu de `const CObject*&`.  Cette modification a été apportée pour mettre le compilateur en conformité avec la norme C.

Le tableau suivant montre d’autres `CObList::GetPrev`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Les résultats de ce programme sont les suivants :

```Output
a CAge at $421C 21
a CAge at $421C 40
```

## <a name="coblistgetsize"></a><a name="getsize"></a>CObList::GetSize

Retourne le nombre d’éléments de liste.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments dans la liste.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments de la liste.

Le tableau suivant montre d’autres `CObList::GetSize`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

## <a name="coblistgettail"></a><a name="gettail"></a>CObList::GetTail

Obtient `CObject` le pointeur qui représente l’élément de queue de cette liste.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Valeur de retour

Voir la description de la valeur de retour pour [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `GetTail`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant montre d’autres `CObList::GetTail`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* vide& GetTail) const; vide\*& GetTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetTail) ) const; CString& GetTail( );**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

## <a name="coblistgettailposition"></a><a name="gettailposition"></a>CObList::GetTailPosition

Obtient la position de l’élément de queue de cette liste; **NULL** si la liste est vide.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si la liste est vide.

Le tableau suivant montre d’autres `CObList::GetTailPosition`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition( ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

## <a name="coblistinsertafter"></a><a name="insertafter"></a>CObList::InsertAfter

Ajoute un élément à cette liste après l’élément à la position spécifiée.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*Position*<br/>
Une valeur POSITION retournée `GetNext` `GetPrev`par `Find` un précédent , , ou appel de fonction de membre.

*nouvel Element*<br/>
Le pointeur d’objet à ajouter à cette liste.

Le tableau suivant montre d’autres `CObList::InsertAfter`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INSERTION POSITIONAprès ( position POSITION** *position* **, vide** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertAfter ( POSITION** *position* **, const CString** `newElement` **&);**<br /><br /> **INSERTION POSITIONAprès (** *position* POSITION , **LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui est la même que le paramètre de *position.*

### <a name="example"></a>Exemple

  Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Les résultats de ce programme sont les suivants :

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

## <a name="coblistinsertbefore"></a><a name="insertbefore"></a>CObList::InsertBefore

Ajoute un élément à cette liste avant l’élément à la position spécifiée.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*Position*<br/>
Une valeur POSITION retournée `GetNext` `GetPrev`par `Find` un précédent , , ou appel de fonction de membre.

*nouvel Element*<br/>
Le pointeur d’objet à ajouter à cette liste.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou la récupération de pointeurs d’objet; NULL si la liste est vide.

Le tableau suivant montre d’autres `CObList::InsertBefore`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertBefore ( position POSITION** *position* **, vide** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertBefore ( POSITION** *position* **, const CString** `newElement` **&);**<br /><br /> **POSITION InsertBefore ( position POSITION** *position* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Les résultats de ce programme sont les suivants :

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

## <a name="coblistisempty"></a><a name="isempty"></a>CObList:IsEmpty

Indique si cette liste ne contient aucun élément.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si cette liste est vide; sinon 0.

Le tableau suivant montre d’autres `CObList::IsEmpty`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty( ) const;**|

### <a name="example"></a>Exemple

  Voir l’exemple pour [RemoveAll](#removeall).

## <a name="coblistremoveall"></a><a name="removeall"></a>CObList::RemoveAll

Supprime tous les éléments de cette liste `CObList` et libère la mémoire associée.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Aucune erreur n’est générée si la liste est déjà vide.

Lorsque vous supprimez `CObList`les éléments d’un, vous supprimez les pointeurs d’objets de la liste. Il est de votre responsabilité de supprimer les objets eux-mêmes.

Le tableau suivant montre d’autres `CObList::RemoveAll`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**vide RemoveAll( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**vide RemoveAll( );**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

## <a name="coblistremoveat"></a><a name="removeat"></a>CObList::RemoveAt

Supprime l’élément spécifié de cette liste.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Paramètres

*Position*<br/>
La position de l’élément à supprimer de la liste.

### <a name="remarks"></a>Notes

Lorsque vous supprimez `CObList`un élément d’un, vous supprimez le pointeur d’objet de la liste. Il est de votre responsabilité de supprimer les objets eux-mêmes.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Le tableau suivant montre d’autres `CObList::RemoveAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**suppression de videAt (position** *position* **POSITION);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**suppression de videAt (position** *position* **POSITION);**|

### <a name="example"></a>Exemple

  Soyez prudent lors de la suppression d’un élément lors d’une itération de liste. L’exemple suivant montre une technique de suppression qui garantit une valeur **POSITION** valide pour [GetNext](#getnext).

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Les résultats de ce programme sont les suivants :

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

## <a name="coblistremovehead"></a><a name="removehead"></a>CObList::RemoveHead

Supprime l’élément de la tête de la liste et y renvoie un pointeur.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Valeur de retour

Le `CObject` pointeur précédemment en tête de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `RemoveHead`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant montre d’autres `CObList::RemoveHead`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**vide\* RemoveHead();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead() );**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

## <a name="coblistremovetail"></a><a name="removetail"></a>CObList::RemoveTail

Supprime l’élément de la queue de la liste et y renvoie un pointeur.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’objet qui était à la queue de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `RemoveTail`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant montre d’autres `CObList::RemoveTail`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**vide\* RemoveTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail( );**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

## <a name="coblistsetat"></a><a name="setat"></a>CObList::SetAt

Définit l’élément à une position donnée.

```cpp
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le POSITION de l’élément à définir.

*nouvel Element*<br/>
Le `CObject` pointeur à écrire sur la liste.

### <a name="remarks"></a>Notes

Une variable de type POSITION est une clé pour la liste. Ce n’est pas la même chose qu’un index, et vous ne pouvez pas fonctionner sur une valeur POSITION vous-même. `SetAt`écrit `CObject` le pointeur à la position spécifiée dans la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Le tableau suivant montre d’autres `CObList::SetAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt ( POSITION** `pos` **, const CString** `newElement` **&);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt ( POSITION** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](#coblist) pour une `CAge` liste de la classe.

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Les résultats de ce programme sont les suivants :

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CStringList](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList, classe](../../mfc/reference/cptrlist-class.md)
