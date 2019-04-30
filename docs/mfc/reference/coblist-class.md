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
ms.openlocfilehash: 2fc3a3643c675394de555f1411030e278bcee775
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388239"
---
# <a name="coblist-class"></a>CObList, classe

fSupports listes ordonnées de non uniques `CObject` pointeurs accessibles séquentiellement ou par le pointeur de valeur.

## <a name="syntax"></a>Syntaxe

```
class CObList : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CObList::CObList](#coblist)|Construit une liste vide pour `CObject` des pointeurs.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObList::AddHead](#addhead)|Ajoute un élément (ou tous les éléments dans une autre liste) au début de la liste (fait une nouvelle tête).|
|[CObList::AddTail](#addtail)|Ajoute un élément (ou tous les éléments dans une autre liste) à la fin de la liste (fait une nouvelle fin).|
|[CObList::Find](#find)|Obtient la position d’un élément spécifié par la valeur de pointeur.|
|[CObList::FindIndex](#findindex)|Obtient la position d’un élément spécifié par un index de base zéro.|
|[CObList::GetAt](#getat)|Obtient l’élément à une position donnée.|
|[CObList::GetCount](#getcount)|Retourne le nombre d’éléments dans cette liste.|
|[CObList::GetHead](#gethead)|Retourne l’élément head de la liste (ne peut pas être vide).|
|[CObList::GetHeadPosition](#getheadposition)|Retourne la position de l’élément head de la liste.|
|[CObList::GetNext](#getnext)|Obtient l’élément suivant pour une itération.|
|[CObList::GetPrev](#getprev)|Obtient l’élément précédent pour une itération.|
|[CObList::GetSize](#getsize)|Retourne le nombre d’éléments dans cette liste.|
|[CObList::GetTail](#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|
|[CObList::GetTailPosition](#gettailposition)|Retourne la position de l’élément de fin de la liste.|
|[CObList::InsertAfter](#insertafter)|Insère un nouvel élément après une position donnée.|
|[CObList::InsertBefore](#insertbefore)|Insère un nouvel élément avant une position donnée.|
|[CObList::IsEmpty](#isempty)|Vérifie si la condition de liste vide (aucun élément).|
|[CObList::RemoveAll](#removeall)|Supprime tous les éléments de cette liste.|
|[CObList::RemoveAt](#removeat)|Supprime un élément de cette liste, spécifiée par position.|
|[CObList::RemoveHead](#removehead)|Supprime l’élément de la tête de la liste.|
|[CObList::RemoveTail](#removetail)|Supprime l’élément à partir de la fin de la liste.|
|[CObList::SetAt](#setat)|Définit l’élément à une position donnée.|

## <a name="remarks"></a>Notes

`CObList` listes se comportent comme les listes à chaînage double.

Une variable de type POSITION est une clé pour la liste. Vous pouvez utiliser une variable POSITION en tant qu’itérateur pour parcourir une liste de manière séquentielle et en tant qu’un signet à un espace réservé. Une position n’est pas identique à un index, toutefois.

Insertion d’éléments est très rapide à la tête de liste, à la fin et à une POSITION connue. Une recherche séquentielle est nécessaire pour rechercher un élément par valeur ou index. Cette recherche peut être lente si la liste est longue.

`CObList` incorpore la macro IMPLEMENT_SERIAL pour prendre en charge la sérialisation et le vidage de ses éléments. Si une liste de `CObject` pointeurs est stocké dans une archive, avec un opérateur d’insertion surchargé ou avec le `Serialize` fonction membre, chaque `CObject` élément est sérialisé à son tour.

Si vous avez besoin d’un dump de l’individu `CObject` éléments dans la liste, vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.

Quand un `CObList` objet est supprimé, ou lorsque ses éléments sont supprimés, uniquement le `CObject` pointeurs sont supprimés, pas les objets qu’ils référencent.

Vous pouvez dériver vos propres classes de `CObList`. Votre nouvelle classe de liste, conçu pour contenir des pointeurs vers les objets dérivés de `CObject`, ajoute de nouveaux membres de données et les nouvelles fonctions membres. Notez que la liste résultante n’est pas strictement type sécurisé, car il autorise l’insertion de n’importe quel `CObject` pointeur.

> [!NOTE]
>  Vous devez utiliser le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro dans l’implémentation de votre classe dérivée si vous prévoyez de sérialiser la liste.

Pour plus d’informations sur l’utilisation de `CObList`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcoll.h

##  <a name="addhead"></a>  CObList::AddHead

Ajoute un nouvel élément ou une liste d’éléments au début de cette liste.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Paramètres

*newElement*<br/>
Le `CObject` pointeur doit être ajouté à cette liste.

*pNewList*<br/>
Un pointeur vers une autre `CObList` liste. Les éléments dans *pNewList* sera ajouté à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version retourne la valeur de la POSITION de l’élément nouvellement inséré.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::AddHead`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddHead( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddHead(const CString&** `newElement` **);**<br /><br /> **POSITION AddHead(LPCTSTR** `newElement` **);**<br /><br /> **void AddHead(CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

### <a name="example"></a>Exemple

  Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Les résultats à partir de ce programme sont les suivantes :

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>  CObList::AddTail

Ajoute un nouvel élément ou une liste d’éléments à la fin de cette liste.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Paramètres

*newElement*<br/>
Le `CObject` pointeur doit être ajouté à cette liste.

*pNewList*<br/>
Un pointeur vers une autre `CObList` liste. Les éléments dans *pNewList* sera ajouté à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version retourne la valeur de la POSITION de l’élément nouvellement inséré.

### <a name="remarks"></a>Notes

La liste peut être vide avant l’opération.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::AddTail`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddTail( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddTail( const CString&** `newElement` **);**<br /><br /> **POSITION AddTail( LPCTSTR** `newElement` **);**<br /><br /> **void AddTail( CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Exemple

  Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Les résultats à partir de ce programme sont les suivantes :

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>  CObList::CObList

Construit un vide `CObject` liste de pointeur.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
La granularité d’allocation de mémoire pour l’extension de la liste.

### <a name="remarks"></a>Notes

Que la liste augmente, la mémoire est allouée en unités de *nBlockSize* entrées. Si une allocation de mémoire échoue, un `CMemoryException` est levée.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::CObList`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList( INT_PTR** `nBlockSize` **= 10 );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>Exemple

  Voici une liste de la `CObject`-classe dérivée `CAge` utilisé dans tous les exemples de collection :

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Voici un exemple de `CObList` l’utilisation du constructeur :

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>  CObList::Find

Recherche dans la liste après l’autre pour rechercher la première `CObject` pointeur correspondant spécifié `CObject` pointeur.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Paramètres

*searchValue*<br/>
Le pointeur d’objet à rechercher dans cette liste.

*startAfter*<br/>
Position de départ pour la recherche.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si l’objet est introuvable.

### <a name="remarks"></a>Notes

Notez que les valeurs de pointeur sont comparées, et pas le contenu des objets.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::Find`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Recherche POSITION (void** <strong>\*</strong> `searchValue` **, POSITION** `startAfter` **= NULL) const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Recherche POSITION (LPCTSTR** `searchValue` **, POSITION** `startAfter` **= NULL) const ;**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>  CObList::FindIndex

Utilise la valeur de *nIndex* en tant qu’index dans la liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro de l’élément de liste doit être recherché.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si *nIndex* est trop grande. (L’infrastructure génère une assertion si *nIndex* est un nombre négatif.)

### <a name="remarks"></a>Notes

Il démarre une analyse séquentielle de la tête de la liste, l’arrêt sur la *n*-ième élément.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::FindIndex`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION FindIndex (INT_PTR** `nIndex` **) const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION FindIndex (INT_PTR** `nIndex` **) const ;**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>  CObList::GetAt

Une variable de type POSITION est une clé pour la liste.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Une valeur POSITION retournée par une précédente `GetHeadPosition` ou `Find` appel de fonction membre.

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour de [GetHead](#gethead).

### <a name="remarks"></a>Notes

Il n’est pas identique à un index, et vous ne peut pas fonctionner sur une valeur POSITION vous-même. `GetAt` Récupère le `CObject` pointeur associé à une position donnée.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetAt`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt (POSITION** *position* **) const ;**<br /><br /> **void\*& GetAt( POSITION** *position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetAt (POSITION** *position* **) const ;**<br /><br /> **CString& GetAt( POSITION** *position* **);**|

### <a name="example"></a>Exemple

  Consultez l’exemple de [FindIndex](#findindex).

##  <a name="getcount"></a>  CObList::GetCount

Obtient le nombre d’éléments dans cette liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur entière qui contient le nombre d’éléments.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetCount`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>  CObList::GetHead

Obtient le `CObject` pointeur qui représente l’élément head de cette liste.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Valeur de retour

Si la liste est accessible via un pointeur vers un `const CObList`, puis `GetHead` retourne un `CObject` pointeur. Cela permet à la fonction être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège donc la liste de toute modification.

Si la liste est accessible directement ou via un pointeur vers un `CObList`, puis `GetHead` retourne une référence à un `CObject` pointeur. Cela permet la fonction à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetHead`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetHead`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead( ) const; void\*& GetHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetHead( ) const; CString& GetHead( );**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

L’exemple suivant illustre l’utilisation de `GetHead` sur le côté gauche d’une instruction d’assignation.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>  CObList::GetHeadPosition

Obtient la position de l’élément head de cette liste.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si la liste est vide.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetHeadPosition`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition( ) const;**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>  CObList::GetNext

Obtient l’élément de liste identifié par *rPosition*, puis définit *rPosition* à la `POSITION` valeur de l’entrée suivante dans la liste.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Une référence à une valeur POSITION retournée par une précédente `GetNext`, `GetHeadPosition`, ou un autre appel de fonction membre.

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour de [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetNext` dans une boucle d’itération en avant si vous établissez la position initiale avec un appel à `GetHeadPosition` ou `Find`.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

Si l’élément récupéré est le dernier dans la liste, puis la nouvelle valeur de *rPosition* est définie sur NULL.

Il est possible de supprimer un élément lors d’une itération. Consultez l’exemple de [RemoveAt](#removeat).

> [!NOTE]
>  À compter de MFC 8.0, la version const de cette méthode a changé pour retourner `const CObject*` au lieu de `const CObject*&`.  Cette modification a été apportée pour mettre le compilateur en conformité avec la norme C++.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetNext`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Exemple

  Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Les résultats à partir de ce programme sont les suivantes :

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>  CObList::GetPrev

Obtient l’élément de liste identifié par *rPosition*, puis définit *rPosition* à la valeur de la POSITION de l’entrée précédente dans la liste.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Une référence à une valeur POSITION retournée par une précédente `GetPrev` ou un autre appel de fonction membre.

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour de [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetPrev` dans une boucle d’itération inverse si vous établissez la position initiale avec un appel à `GetTailPosition` ou `Find`.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

Si l’élément récupéré est le premier dans la liste, puis la nouvelle valeur de *rPosition* est définie sur NULL.

> [!NOTE]
>  À compter de MFC 8.0, la version const de cette méthode a changé pour retourner `const CObject*` au lieu de `const CObject*&`.  Cette modification a été apportée pour mettre le compilateur en conformité avec la norme C++.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetPrev`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Exemple

  Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Les résultats à partir de ce programme sont les suivantes :

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>  CObList::GetSize

Retourne le nombre d’éléments de liste.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments de la liste.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans la liste.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetSize`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize () const ;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>  CObList::GetTail

Obtient le `CObject` pointeur qui représente l’élément de fin de cette liste.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Valeur de retour

Consultez la description de la valeur de retour de [GetHead](#gethead).

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetTail`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetTail`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail( ) const; void\*& GetTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetTail( ) const; CString& GetTail( );**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>  CObList::GetTailPosition

Obtient la position de l’élément de fin de cette liste. **NULL** si la liste est vide.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si la liste est vide.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::GetTailPosition`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition( ) const;**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>  CObList::InsertAfter

Ajoute un élément à cette liste après l’élément à la position spécifiée.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Une valeur POSITION retournée par une précédente `GetNext`, `GetPrev`, ou `Find` appel de fonction membre.

*newElement*<br/>
Le pointeur d’objet à ajouter à cette liste.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::InsertAfter`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertAfter( POSITION** *position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertAfter( POSITION** *position* **, const CString&** `newElement` **);**<br /><br /> **POSITION InsertAfter( POSITION** *position* **, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui est le même que le *position* paramètre.

### <a name="example"></a>Exemple

  Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Les résultats à partir de ce programme sont les suivantes :

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>  CObList::InsertBefore

Ajoute un élément à cette liste avant l’élément à la position spécifiée.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
Une valeur POSITION retournée par une précédente `GetNext`, `GetPrev`, ou `Find` appel de fonction membre.

*newElement*<br/>
Le pointeur d’objet à ajouter à cette liste.

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si la liste est vide.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::InsertBefore`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertBefore( POSITION** *position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertBefore( POSITION** *position* **, const CString&** `newElement` **);**<br /><br /> **POSITION InsertBefore( POSITION** *position* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Exemple

  Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Les résultats à partir de ce programme sont les suivantes :

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>  CObList::IsEmpty

Indique si cette liste ne contient aucun élément.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si cette liste est vide. sinon 0.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::IsEmpty`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty( ) const;**|

### <a name="example"></a>Exemple

  Consultez l’exemple de [RemoveAll](#removeall).

##  <a name="removeall"></a>  CObList::RemoveAll

Supprime tous les éléments de cette liste et libère associé `CObList` mémoire.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Aucune erreur n’est générée si la liste est déjà vide.

Lorsque vous supprimez des éléments à partir d’un `CObList`, vous supprimez les pointeurs d’objet de la liste. Il vous incombe de supprimer les objets eux-mêmes.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::RemoveAll`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>  CObList::RemoveAt

Supprime l’élément spécifié à partir de cette liste.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Paramètres

*position*<br/>
La position de l’élément à supprimer de la liste.

### <a name="remarks"></a>Notes

Lorsque vous supprimez un élément à partir d’un `CObList`, vous supprimez le pointeur d’objet de la liste. Il vous incombe de supprimer les objets eux-mêmes.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::RemoveAt`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt( POSITION** *position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt( POSITION** *position* **);**|

### <a name="example"></a>Exemple

  Soyez prudent lors de la suppression d’un élément pendant une itération de la liste. L’exemple suivant montre une technique de suppression qui garantit une valide **POSITION** valeur [GetNext](#getnext).

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Les résultats à partir de ce programme sont les suivantes :

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>  CObList::RemoveHead

Supprime l’élément de la tête de la liste et retourne un pointeur vers elle.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Valeur de retour

Le `CObject` pointeur précédemment au début de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveHead`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::RemoveHead`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead( );**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>  CObList::RemoveTail

Supprime l’élément de la fin de la liste et retourne un pointeur vers elle.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet qui a été à la fin de la liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveTail`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::RemoveTail`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail( );**|

### <a name="example"></a>Exemple

Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>  CObList::SetAt

Définit l’élément à une position donnée.

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
La POSITION de l’élément à définir.

*newElement*<br/>
Le `CObject` pointeur à écrire dans la liste.

### <a name="remarks"></a>Notes

Une variable de type POSITION est une clé pour la liste. Il n’est pas identique à un index, et vous ne peut pas fonctionner sur une valeur POSITION vous-même. `SetAt` écrit le `CObject` pointeur vers la position spécifiée dans la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.

Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObList::SetAt`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt( POSITION** `pos` **, const CString&** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt( POSITION** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Exemple

  Consultez [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Les résultats à partir de ce programme sont les suivantes :

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CStringList, classe](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList, classe](../../mfc/reference/cptrlist-class.md)
