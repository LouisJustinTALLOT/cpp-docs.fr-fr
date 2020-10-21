---
title: CObList (classe)
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
ms.openlocfilehash: a13363ef9b200051c26781ab6e9870a10de06d88
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274584"
---
# <a name="coblist-class"></a>CObList (classe)

Prend en charge les listes ordonnées de `CObject` pointeurs non uniques accessibles séquentiellement ou par valeur de pointeur.

## <a name="syntax"></a>Syntaxe

```
class CObList : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CObList :: CObList](#coblist)|Construit une liste vide pour les `CObject` pointeurs.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObList :: AddHead](#addhead)|Ajoute un élément (ou tous les éléments d’une autre liste) au début de la liste (crée un nouvel en-tête).|
|[CObList :: AddTail](#addtail)|Ajoute un élément (ou tous les éléments d’une autre liste) à la fin de la liste (crée une nouvelle fin).|
|[CObList :: find](#find)|Obtient la position d’un élément spécifié par la valeur de pointeur.|
|[CObList :: FindIndex](#findindex)|Obtient la position d’un élément spécifié par un index de base zéro.|
|[CObList :: GetAt](#getat)|Obtient l’élément à une position donnée.|
|[CObList :: GetCount](#getcount)|Retourne le nombre d’éléments de cette liste.|
|[CObList :: GetHead](#gethead)|Retourne l’élément head de la liste (ne peut pas être vide).|
|[CObList :: GetHeadPosition](#getheadposition)|Retourne la position de l’élément head de la liste.|
|[CObList :: GetNext](#getnext)|Obtient l’élément suivant pour l’itération.|
|[CObList :: GetPrev](#getprev)|Obtient l’élément précédent pour l’itération.|
|[CObList :: Deis](#getsize)|Retourne le nombre d’éléments de cette liste.|
|[CObList :: GetTail](#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|
|[CObList :: GetTailPosition](#gettailposition)|Retourne la position de l’élément de fin de la liste.|
|[CObList :: InsertAfter](#insertafter)|Insère un nouvel élément après une position donnée.|
|[CObList :: InsertBefore](#insertbefore)|Insère un nouvel élément avant une position donnée.|
|[CObList :: IsEmpty](#isempty)|Teste la condition de liste vide (aucun élément).|
|[CObList :: RemoveAll](#removeall)|Supprime tous les éléments de cette liste.|
|[CObList :: RemoveAt](#removeat)|Supprime un élément de cette liste, spécifié par position.|
|[CObList :: RemoveHead](#removehead)|Supprime l’élément du début de la liste.|
|[CObList :: RemoveTail](#removetail)|Supprime l’élément de la fin de la liste.|
|[CObList :: SetAt](#setat)|Définit l’élément à une position donnée.|

## <a name="remarks"></a>Notes

`CObList` les listes se comportent comme des listes doublement liées.

Une variable de type POSITION est une clé pour la liste. Vous pouvez utiliser une variable POSITION en tant qu’itérateur pour parcourir une liste de façon séquentielle et comme signet pour contenir un emplacement. Toutefois, une position n’est pas identique à un index.

L’insertion d’élément est très rapide à l’en-tête de liste, à la fin et à une POSITION connue. Une recherche séquentielle est nécessaire pour rechercher un élément par valeur ou par index. Cette recherche peut être lente si la liste est longue.

`CObList` incorpore la macro IMPLEMENT_SERIAL pour prendre en charge la sérialisation et le vidage de ses éléments. Si une liste de `CObject` pointeurs est stockée dans une archive, soit avec un opérateur d’insertion surchargé, soit avec la `Serialize` fonction membre, chaque `CObject` élément est sérialisé à son tour.

Si vous avez besoin d’un vidage d' `CObject` éléments individuels dans la liste, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Lorsqu’un `CObList` objet est supprimé ou que ses éléments sont supprimés, seuls les `CObject` pointeurs sont supprimés, pas les objets qu’ils référencent.

Vous pouvez dériver vos propres classes à partir de `CObList` . Votre nouvelle classe de liste, conçue pour contenir des pointeurs vers des objets dérivés de `CObject` , ajoute de nouveaux membres de données et de nouvelles fonctions membres. Notez que la liste résultante n’est pas strictement de type sécurisé, car elle permet l’insertion de n’importe quel `CObject` pointeur.

> [!NOTE]
> Vous devez utiliser la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) dans l’implémentation de votre classe dérivée si vous envisagez de sérialiser la liste.

Pour plus d’informations sur l’utilisation de `CObList` , consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcoll. h

## <a name="coblistaddhead"></a><a name="addhead"></a> CObList :: AddHead

Ajoute un nouvel élément ou une liste d’éléments au début de cette liste.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Paramètres

*newElement*<br/>
`CObject`Pointeur à ajouter à cette liste.

*pNewList*<br/>
Pointeur vers une autre `CObList` liste. Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version retourne la valeur de POSITION de l’élément qui vient d’être inséré.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::AddHead` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position AddHead (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position AddHead (const CString&** `newElement` **);**<br /><br /> **Position AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Les résultats de ce programme sont les suivants :

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

## <a name="coblistaddtail"></a><a name="addtail"></a> CObList :: AddTail

Ajoute un nouvel élément ou une liste d’éléments à la fin de cette liste.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Paramètres

*newElement*<br/>
`CObject`Pointeur à ajouter à cette liste.

*pNewList*<br/>
Pointeur vers une autre `CObList` liste. Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version retourne la valeur de POSITION de l’élément qui vient d’être inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::AddTail` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position AddTail (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position AddTail (const CString&** `newElement` **);**<br /><br /> **Position AddTail (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Les résultats de ce programme sont les suivants :

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

## <a name="coblistcoblist"></a><a name="coblist"></a> CObList :: CObList

Construit une liste de `CObject` pointeurs vide.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Granularité d’allocation de mémoire pour étendre la liste.

### <a name="remarks"></a>Notes

À mesure que la liste croît, la mémoire est allouée en unités d’entrées *nBlockSize* . En cas d’échec d’une allocation de mémoire, une `CMemoryException` exception est levée.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::CObList` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Exemple

  Vous trouverez ci-dessous une liste de la `CObject` classe dérivée de `CAge` utilisée dans tous les exemples de collection :

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Voici un exemple d' `CObList` utilisation de constructeur :

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

## <a name="coblistfind"></a><a name="find"></a> CObList :: find

Recherche séquentiellement la liste pour trouver le premier `CObject` pointeur correspondant au `CObject` pointeur spécifié.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Paramètres

*searchValue*<br/>
Pointeur d’objet à rechercher dans cette liste.

*startAfter*<br/>
Position de départ de la recherche.

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si l’objet est introuvable.

### <a name="remarks"></a>Notes

Notez que les valeurs de pointeur sont comparées, et non le contenu des objets.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::Find` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position Rechercher (void)** <strong>\*</strong> `searchValue` **, Position** `startAfter` **= Null) const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position Find (LPCTSTR** `searchValue` **, position** `startAfter` **= null) const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

## <a name="coblistfindindex"></a><a name="findindex"></a> CObList :: FindIndex

Utilise la valeur de *nIndex* en tant qu’index dans la liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro de l’élément de liste à trouver.

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si *nIndex* est trop grand. (L’infrastructure génère une assertion si *nIndex* est négatif.)

### <a name="remarks"></a>Notes

Il démarre une analyse séquentielle à partir du début de la liste, en arrêtant sur le *n*ième élément.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::FindIndex` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position FindIndex (INT_PTR** `nIndex` **) const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position FindIndex (INT_PTR** `nIndex` **) const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

## <a name="coblistgetat"></a><a name="getat"></a> CObList :: GetAt

Une variable de type POSITION est une clé pour la liste.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Valeur de POSITION retournée par un `GetHeadPosition` `Find` appel de fonction membre ou précédent.

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour pour [GetHead](#gethead).

### <a name="remarks"></a>Notes

Ce n’est pas le même qu’un index, et vous ne pouvez pas utiliser une valeur POSITION vous-même. `GetAt` Récupère le `CObject` pointeur associé à une position donnée.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetAt` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void \*& GetAt (** *position position* **) const ;**<br /><br /> **void \*& GetAt (position position** *position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetAt (** *position position* **) const ;**<br /><br /> **CString& GetAt (POSITION position** *position* **);**|

### <a name="example"></a>Exemple

  Consultez l’exemple de [FindIndex](#findindex).

## <a name="coblistgetcount"></a><a name="getcount"></a> CObList :: GetCount

Obtient le nombre d’éléments de cette liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur entière contenant le nombre d’éléments.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetCount` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount () const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

## <a name="coblistgethead"></a><a name="gethead"></a> CObList :: GetHead

Obtient le `CObject` pointeur qui représente l’élément head de cette liste.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Valeur de retour

Si la liste est accessible via un pointeur vers `const CObList` , `GetHead` retourne un `CObject` pointeur. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger ainsi la liste contre toute modification.

Si la liste est accessible directement ou via un pointeur vers `CObList` , `GetHead` retourne une référence à un `CObject` pointeur. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetHead` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetHead` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void \*& GetHead () const ; void \*& GetHead ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetHead () const ; CString& GetHead ();**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

L’exemple suivant illustre l’utilisation de `GetHead` sur le côté gauche d’une instruction d’assignation.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

## <a name="coblistgetheadposition"></a><a name="getheadposition"></a> CObList :: GetHeadPosition

Obtient la position de l’élément head de cette liste.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si la liste est vide.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetHeadPosition` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition () const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

## <a name="coblistgetnext"></a><a name="getnext"></a> CObList :: GetNext

Obtient l’élément de liste identifié par *rPosition*, puis affecte à *rPosition* la `POSITION` valeur de l’entrée suivante dans la liste.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Référence à une valeur de POSITION retournée par un `GetNext` `GetHeadPosition` appel de fonction membre précédent, ou autre.

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour pour [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetNext` dans une boucle d’itération anticipée si vous établissez la position initiale avec un appel à `GetHeadPosition` ou `Find` .

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Si l’élément récupéré est le dernier de la liste, la nouvelle valeur de *rPosition* est définie sur null.

Il est possible de supprimer un élément pendant une itération. Consultez l’exemple de [RemoveAt](#removeat).

> [!NOTE]
> À partir de MFC 8,0, la version const de cette méthode a changé pour retourner `const CObject*` au lieu de `const CObject*&` .  Cette modification a été apportée pour mettre le compilateur en conformité avec la norme C++.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetNext` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Les résultats de ce programme sont les suivants :

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

## <a name="coblistgetprev"></a><a name="getprev"></a> CObList :: GetPrev

Obtient l’élément de liste identifié par *rPosition*, puis affecte à *rPosition* la valeur de position de l’entrée précédente dans la liste.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Référence à une valeur de POSITION retournée par un `GetPrev` appel de fonction membre ou précédent.

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour pour [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetPrev` dans une boucle d’itération inverse si vous établissez la position initiale avec un appel à `GetTailPosition` ou `Find` .

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Si l’élément récupéré est le premier de la liste, la nouvelle valeur de *rPosition* est définie sur null.

> [!NOTE]
> À partir de MFC 8,0, la version const de cette méthode a changé pour retourner `const CObject*` au lieu de `const CObject*&` .  Cette modification a été apportée pour mettre le compilateur en conformité avec la norme C++.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetPrev` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Les résultats de ce programme sont les suivants :

```Output
a CAge at $421C 21
a CAge at $421C 40
```

## <a name="coblistgetsize"></a><a name="getsize"></a> CObList :: Deis

Retourne le nombre d’éléments de liste.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments dans la liste.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans la liste.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetSize` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTRs () const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTRs () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

## <a name="coblistgettail"></a><a name="gettail"></a> CObList :: GetTail

Obtient le `CObject` pointeur qui représente l’élément de fin de cette liste.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour pour [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetTail` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetTail` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void \*& GetTail () const ; void \*& GetTail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetTail () const ; CString& GetTail ();**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

## <a name="coblistgettailposition"></a><a name="gettailposition"></a> CObList :: GetTailPosition

Obtient la position de l’élément de fin de cette liste ; **Null** si la liste est vide.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si la liste est vide.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::GetTailPosition` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition () const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

## <a name="coblistinsertafter"></a><a name="insertafter"></a> CObList :: InsertAfter

Ajoute un élément à cette liste après l’élément à la position spécifiée.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Valeur de POSITION retournée par un `GetNext` `GetPrev` appel de fonction membre, ou précédent `Find` .

*newElement*<br/>
Pointeur d’objet à ajouter à cette liste.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::InsertAfter` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position InsertAfter (** *position position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertAfter (** *position position* **, const CString&** `newElement` **);**<br /><br /> **Position InsertAfter (** *position position* **, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui est identique au paramètre *position* .

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Les résultats de ce programme sont les suivants :

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

## <a name="coblistinsertbefore"></a><a name="insertbefore"></a> CObList :: InsertBefore

Ajoute un élément à cette liste avant l’élément à la position spécifiée.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Valeur de POSITION retournée par un `GetNext` `GetPrev` appel de fonction membre, ou précédent `Find` .

*newElement*<br/>
Pointeur d’objet à ajouter à cette liste.

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui peut être utilisée pour la récupération de l’itération ou du pointeur d’objet ; NULL si la liste est vide.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::InsertBefore` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position InsertBefore (** *position position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertBefore (** *position position* **, const CString&** `newElement` **);**<br /><br /> **Position InsertBefore (** *position position* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Les résultats de ce programme sont les suivants :

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

## <a name="coblistisempty"></a><a name="isempty"></a> CObList :: IsEmpty

Indique si cette liste ne contient aucun élément.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si cette liste est vide ; Sinon, 0.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::IsEmpty` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty () const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty () const ;**|

### <a name="example"></a>Exemple

  Consultez l’exemple pour [RemoveAll](#removeall).

## <a name="coblistremoveall"></a><a name="removeall"></a> CObList :: RemoveAll

Supprime tous les éléments de cette liste et libère la mémoire associée `CObList` .

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Aucune erreur n’est générée si la liste est déjà vide.

Lorsque vous supprimez des éléments d’un `CObList` , vous supprimez les pointeurs d’objet de la liste. Il vous incombe de supprimer les objets eux-mêmes.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::RemoveAll` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

## <a name="coblistremoveat"></a><a name="removeat"></a> CObList :: RemoveAt

Supprime l’élément spécifié de cette liste.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Position de l’élément à supprimer de la liste.

### <a name="remarks"></a>Notes

Lorsque vous supprimez un élément d’une `CObList` , vous supprimez le pointeur d’objet de la liste. Il vous incombe de supprimer les objets eux-mêmes.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::RemoveAt` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (** *position position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (** *position position* **);**|

### <a name="example"></a>Exemple

  Soyez prudent lors de la suppression d’un élément pendant une itération de liste. L’exemple suivant illustre une technique de suppression qui garantit une valeur **position** valide pour [GetNext](#getnext).

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Les résultats de ce programme sont les suivants :

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

## <a name="coblistremovehead"></a><a name="removehead"></a> CObList :: RemoveHead

Supprime l’élément de l’en-tête de la liste et retourne un pointeur vers celui-ci.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Valeur de retour

`CObject`Pointeur précédemment à l’en-tête de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveHead` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::RemoveHead` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void \* RemoveHead ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead ();**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

## <a name="coblistremovetail"></a><a name="removetail"></a> CObList :: RemoveTail

Supprime l’élément de la fin de la liste et retourne un pointeur vers celui-ci.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet qui était à la fin de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveTail` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::RemoveTail` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void \* RemoveTail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail ();**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

## <a name="coblistsetat"></a><a name="setat"></a> CObList :: SetAt

Définit l’élément à une position donnée.

```cpp
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
POSITION de l’élément à définir.

*newElement*<br/>
`CObject`Pointeur à écrire dans la liste.

### <a name="remarks"></a>Notes

Une variable de type POSITION est une clé pour la liste. Ce n’est pas le même qu’un index, et vous ne pouvez pas utiliser une valeur POSITION vous-même. `SetAt` écrit le `CObject` pointeur à la position spécifiée dans la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Le tableau suivant présente d’autres fonctions membres similaires à `CObList::SetAt` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (position** `pos` **, const CString&** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (position** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Les résultats de ce programme sont les suivants :

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CStringList, classe](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList, classe](../../mfc/reference/cptrlist-class.md)
