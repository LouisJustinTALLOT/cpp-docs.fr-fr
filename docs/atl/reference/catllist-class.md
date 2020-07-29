---
title: CAtlList, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 15830a30e8236a13f3911d1b84d3727d3246fc0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226670"
---
# <a name="catllist-class"></a>CAtlList, classe

Cette classe fournit des méthodes pour créer et gérer un objet de liste.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

### <a name="parameters"></a>Paramètres

*Envoyer*<br/>
Type de l’élément.

*ETraits*<br/>
Code utilisé pour copier ou déplacer des éléments. Pour plus d’informations, consultez la [classe CElementTraits](../../atl/reference/celementtraits-class.md) .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|Constructeur.|
|[CAtlList :: ~ CAtlList](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|Appelez cette méthode pour ajouter un élément au début de la liste.|
|[CAtlList::AddHeadList](#addheadlist)|Appelez cette méthode pour ajouter une liste existante au début de la liste.|
|[CAtlList :: AddTail](#addtail)|Appelez cette méthode pour ajouter un élément à la fin de cette liste.|
|[CAtlList::AddTailList](#addtaillist)|Appelez cette méthode pour ajouter une liste existante à la fin de cette liste.|
|[CAtlList :: AssertValid](#assertvalid)|Appelez cette méthode pour confirmer que la liste est valide.|
|[CAtlList :: find](#find)|Appelez cette méthode pour Rechercher l’élément spécifié dans la liste.|
|[CAtlList :: FindIndex](#findindex)|Appelez cette méthode pour obtenir la position d’un élément, en fonction d’une valeur d’index.|
|[CAtlList :: GetAt](#getat)|Appelez cette méthode pour retourner l’élément à une position spécifiée dans la liste.|
|[CAtlList :: GetCount](#getcount)|Appelez cette méthode pour retourner le nombre d’objets de la liste.|
|[CAtlList::GetHead](#gethead)|Appelez cette méthode pour retourner l’élément au début de la liste.|
|[CAtlList::GetHeadPosition](#getheadposition)|Appelez cette méthode pour obtenir la position du début de la liste.|
|[CAtlList :: GetNext](#getnext)|Appelez cette méthode pour retourner l’élément suivant de la liste.|
|[CAtlList::GetPrev](#getprev)|Appelez cette méthode pour retourner l’élément précédent de la liste.|
|[CAtlList::GetTail](#gettail)|Appelez cette méthode pour retourner l’élément à la fin de la liste.|
|[CAtlList::GetTailPosition](#gettailposition)|Appelez cette méthode pour obtenir la position de la fin de la liste.|
|[CAtlList :: InsertAfter](#insertafter)|Appelez cette méthode pour insérer un nouvel élément dans la liste après la position spécifiée.|
|[CAtlList :: InsertBefore](#insertbefore)|Appelez cette méthode pour insérer un nouvel élément dans la liste avant la position spécifiée.|
|[CAtlList :: IsEmpty](#isempty)|Appelez cette méthode pour déterminer si la liste est vide.|
|[CAtlList::MoveToHead](#movetohead)|Appelez cette méthode pour déplacer l’élément spécifié vers le début de la liste.|
|[CAtlList::MoveToTail](#movetotail)|Appelez cette méthode pour déplacer l’élément spécifié à la fin de la liste.|
|[CAtlList :: RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments de la liste.|
|[CAtlList :: RemoveAt](#removeat)|Appelez cette méthode pour supprimer un élément unique de la liste.|
|[CAtlList::RemoveHead](#removehead)|Appelez cette méthode pour supprimer l’élément au début de la liste.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Appelez cette méthode pour supprimer l’élément au début de la liste sans retourner de valeur.|
|[CAtlList::RemoveTail](#removetail)|Appelez cette méthode pour supprimer l’élément à la fin de la liste.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Appelez cette méthode pour supprimer l’élément à la fin de la liste sans retourner de valeur.|
|[CAtlList :: SetAt](#setat)|Appelez cette méthode pour définir la valeur de l’élément à une position donnée dans la liste.|
|[CAtlList::SwapElements](#swapelements)|Appelez cette méthode pour échanger des éléments dans la liste.|

## <a name="remarks"></a>Notes

La `CAtlList` classe prend en charge les listes ordonnées d’objets non uniques accessibles séquentiellement ou par valeur. `CAtlList`les listes se comportent comme des listes de liens doubles. Chaque liste a un début et une fin, et de nouveaux éléments (ou listes dans certains cas) peuvent être ajoutés à l’une ou l’autre des extrémités de la liste, ou insérés avant ou après des éléments spécifiques.

La plupart des `CAtlList` méthodes utilisent une valeur position. Cette valeur est utilisée par les méthodes pour faire référence à l’emplacement de mémoire réel où les éléments sont stockés, et ne doit pas être calculée ou prédite directement. S’il est nécessaire d’accéder au *n*ième élément de la liste, la méthode [CAtlList :: FindIndex](#findindex) retourne la valeur de position correspondante pour un index donné. Les méthodes [CAtlList :: GetNext](#getnext) et [CAtlList :: GetPrev](#getprev) peuvent être utilisées pour itérer au sein des objets de la liste.

Pour plus d’informations sur les classes de collection disponibles avec ATL, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead

Appelez cette méthode pour ajouter un élément au début de la liste.

```cpp
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*appartient*<br/>
Nouvel élément.

### <a name="return-value"></a>Valeur de retour

Retourne la position de l’élément qui vient d’être ajouté.

### <a name="remarks"></a>Notes

Si la première version est utilisée, un élément vide est créé à l’aide de son constructeur par défaut, plutôt que son constructeur de copie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

Appelez cette méthode pour ajouter une liste existante au début de la liste.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Paramètres

*plNew*<br/>
Liste à ajouter.

### <a name="remarks"></a>Notes

La liste désignée par *plNew* est insérée au début de la liste existante. Dans les versions Debug, un échec d’assertion se produit si *plNew* est égal à null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList :: AddTail

Appelez cette méthode pour ajouter un élément à la fin de cette liste.

```cpp
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*appartient*<br/>
Élément à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne la POSITION de l’élément qui vient d’être ajouté.

### <a name="remarks"></a>Notes

Si la première version est utilisée, un élément vide est créé à l’aide de son constructeur par défaut, plutôt que son constructeur de copie. L’élément est ajouté à la fin de la liste et devient donc la fin. Cette méthode peut être utilisée avec une liste vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

Appelez cette méthode pour ajouter une liste existante à la fin de cette liste.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Paramètres

*plNew*<br/>
Liste à ajouter.

### <a name="remarks"></a>Notes

La liste désignée par *plNew* est insérée après le dernier élément (le cas échéant) dans l’objet de liste. Le dernier élément de la liste *plNew* devient donc la fin. Dans les versions Debug, un échec d’assertion se produit si *plNew* est égal à null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList :: AssertValid

Appelez cette méthode pour confirmer que la liste est valide.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Notes

Dans les versions Debug, un échec d’assertion se produit si l’objet de liste n’est pas valide. Pour être valide, une liste vide doit avoir à la fois la tête et la fin pointant vers la valeur NULL, et une liste qui n’est pas vide doit avoir à la fois la tête et la fin pointant vers des adresses valides.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

Constructeur.

```cpp
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

Constructeur de l' `CAtlList` objet. La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Les tailles de bloc plus volumineuses réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList :: ~ CAtlList

Destructeur.

```cpp
~CAtlList() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, y compris un appel à [CAtlList :: RemoveAll](#removeall) pour supprimer tous les éléments de la liste.

Dans les versions Debug, un échec d’assertion se produit si la liste contient toujours des éléments après l’appel à `RemoveAll` .

## <a name="catllistfind"></a><a name="find"></a>CAtlList :: find

Appelez cette méthode pour Rechercher l’élément spécifié dans la liste.

```cpp
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*appartient*<br/>
Élément à rechercher dans la liste.

*posStartAfter*<br/>
Position de départ de la recherche. Si aucune valeur n’est spécifiée, la recherche commence par l’élément head.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de POSITION de l’élément s’il est trouvé, sinon retourne la valeur NULL.

### <a name="remarks"></a>Notes

Dans les versions Debug, un échec d’assertion se produit si l’objet de liste n’est pas valide ou si la valeur *posStartAfter* est hors limites.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList :: FindIndex

Appelez cette méthode pour obtenir la position d’un élément, en fonction d’une valeur d’index.

```cpp
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
Index de base zéro de l’élément de liste requis.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de POSITION correspondante, ou NULL si *IElement* est hors limites.

### <a name="remarks"></a>Notes

Cette méthode retourne la POSITION correspondant à une valeur d’index donnée, ce qui permet d’accéder au *n*ième élément de la liste.

Dans les versions Debug, un échec d’assertion se produit si l’objet de liste n’est pas valide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList :: GetAt

Appelez cette méthode pour retourner l’élément à une position spécifiée dans la liste.

```cpp
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Valeur de POSITION spécifiant un élément particulier.

### <a name="return-value"></a>Valeur de retour

Référence à l’élément ou copie de celui-ci.

### <a name="remarks"></a>Notes

Si la liste est **`const`** , `GetAt` retourne une copie de l’élément. Cela permet d’utiliser la méthode uniquement à droite d’une instruction d’assignation et de protéger la liste contre toute modification.

Si la liste n’est pas **`const`** , `GetAt` retourne une référence à l’élément. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

Dans les versions Debug, un échec d’assertion se produit si *pos* est égal à null.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CAtlList :: FindIndex](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList :: GetCount

Appelez cette méthode pour retourner le nombre d’objets de la liste.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d'éléments figurant dans la liste.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead

Appelez cette méthode pour retourner l’élément au début de la liste.

```cpp
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une référence à, ou une copie de, l’élément au début de la liste.

### <a name="remarks"></a>Notes

Si la liste est **`const`** , `GetHead` retourne une copie de l’élément au début de la liste. Cela permet d’utiliser la méthode uniquement à droite d’une instruction d’assignation et de protéger la liste contre toute modification.

Si la liste n’est pas **`const`** , `GetHead` retourne une référence à l’élément situé à l’en-tête de la liste. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

Dans les versions Debug, un échec d’assertion se produit si le début de la liste pointe vers NULL.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: AddHead](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

Appelez cette méthode pour obtenir la position du début de la liste.

```cpp
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de POSITION correspondant à l’élément au début de la liste.

### <a name="remarks"></a>Notes

Si la liste est vide, la valeur retournée est NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList :: GetNext

Appelez cette méthode pour retourner l’élément suivant de la liste.

```cpp
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Valeur de POSITION, retournée par un appel précédent à `GetNext` , [CAtlList :: GetHeadPosition](#getheadposition)ou autre `CAtlList` méthode.

### <a name="return-value"></a>Valeur de retour

Si la liste est **`const`** , `GetNext` retourne une copie de l’élément suivant de la liste. Cela permet d’utiliser la méthode uniquement à droite d’une instruction d’assignation et de protéger la liste contre toute modification.

Si la liste n’est pas **`const`** , `GetNext` retourne une référence à l’élément suivant de la liste. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Le compteur de POSITION, *pos*, est mis à jour pour pointer vers l’élément suivant de la liste, ou null s’il n’y a plus d’éléments. Dans les versions Debug, un échec d’assertion se produit si *pos* est égal à null.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev

Appelez cette méthode pour retourner l’élément précédent de la liste.

```cpp
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Valeur de POSITION, retournée par un appel précédent à `GetPrev` , [CAtlList :: GetTailPosition](#gettailposition)ou autre `CAtlList` méthode.

### <a name="return-value"></a>Valeur de retour

Si la liste est **`const`** , `GetPrev` retourne une copie d’un élément de la liste. Cela permet d’utiliser la méthode uniquement à droite d’une instruction d’assignation et de protéger la liste contre toute modification.

Si la liste n’est pas **`const`** , `GetPrev` retourne une référence à un élément de la liste. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Le compteur de POSITION, *pos*, est mis à jour pour pointer vers l’élément précédent de la liste, ou null s’il n’y a plus d’éléments. Dans les versions Debug, un échec d’assertion se produit si *pos* est égal à null.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail

Appelez cette méthode pour retourner l’élément à la fin de la liste.

```cpp
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une référence à ou une copie de l’élément à la fin de la liste.

### <a name="remarks"></a>Notes

Si la liste est **`const`** , `GetTail` retourne une copie de l’élément au début de la liste. Cela permet d’utiliser la méthode uniquement à droite d’une instruction d’assignation et de protéger la liste contre toute modification.

Si la liste n’est pas **`const`** , `GetTail` retourne une référence à l’élément situé à l’en-tête de la liste. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

Dans les versions Debug, un échec d’assertion se produit si la fin de la liste pointe vers la valeur NULL.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: AddTail](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

Appelez cette méthode pour obtenir la position de la fin de la liste.

```cpp
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de POSITION correspondant à l’élément à la fin de la liste.

### <a name="remarks"></a>Notes

Si la liste est vide, la valeur retournée est NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

Type utilisé lorsqu’un élément est passé comme argument d’entrée.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList :: InsertAfter

Appelez cette méthode pour insérer un nouvel élément dans la liste après la position spécifiée.

```cpp
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Valeur de POSITION après laquelle le nouvel élément sera inséré.

*appartient*<br/>
Élément à insérer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de POSITION du nouvel élément.

### <a name="remarks"></a>Notes

Dans les versions Debug, un échec d’assertion se produit si la liste n’est pas valide, si l’insertion échoue ou si une tentative d’insertion de l’élément après la fin de l’opération est effectuée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList :: InsertBefore

Appelez cette méthode pour insérer un nouvel élément dans la liste avant la position spécifiée.

```cpp
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Le nouvel élément sera inséré dans la liste avant cette valeur de POSITION.

*appartient*<br/>
Élément à insérer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de POSITION du nouvel élément.

### <a name="remarks"></a>Notes

Dans les versions Debug, un échec d’assertion se produit si la liste n’est pas valide, si l’insertion échoue ou si une tentative est faite pour insérer l’élément avant l’en-tête.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList :: IsEmpty

Appelez cette méthode pour déterminer si la liste est vide.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si la liste ne contient aucun objet ; sinon, false.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

Appelez cette méthode pour déplacer l’élément spécifié vers le début de la liste.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Valeur de POSITION de l’élément à déplacer.

### <a name="remarks"></a>Notes

L’élément spécifié est déplacé de sa position actuelle jusqu’à l’en-tête de la liste. Dans les versions Debug, un échec d’assertion se produit si *pos* est égal à null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

Appelez cette méthode pour déplacer l’élément spécifié à la fin de la liste.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Valeur de POSITION de l’élément à déplacer.

### <a name="remarks"></a>Notes

L’élément spécifié est déplacé de sa position actuelle jusqu’à la fin de la liste. Dans les versions Debug, un échec d’assertion se produit si *pos* est égal à null.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList :: RemoveAll

Appelez cette méthode pour supprimer tous les éléments de la liste.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Cette méthode supprime tous les éléments de la liste et libère la mémoire allouée. Dans les builds de débogues, un ATLASSERT est déclenché si tous les éléments ne sont pas supprimés ou si la structure de la liste est endommagée.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList :: RemoveAt

Appelez cette méthode pour supprimer un élément unique de la liste.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Valeur de POSITION de l’élément à supprimer.

### <a name="remarks"></a>Notes

L’élément référencé par *pos* est supprimé et la mémoire est libérée. Il est acceptable d’utiliser `RemoveAt` pour supprimer l’en-tête ou la fin de la liste.

Dans les versions Debug, un échec d’assertion se produit si la liste n’est pas valide ou si la suppression de l’élément entraîne l’accès à la mémoire par la liste qui ne fait pas partie de la structure de la liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

Appelez cette méthode pour supprimer l’élément au début de la liste.

```cpp
E RemoveHead();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’élément au début de la liste.

### <a name="remarks"></a>Notes

L’élément Head est supprimé de la liste, et la mémoire est libérée. Une copie de l’élément est retournée. Dans les versions Debug, un échec d’assertion se produit si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

Appelez cette méthode pour supprimer l’élément au début de la liste sans retourner de valeur.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Notes

L’élément Head est supprimé de la liste, et la mémoire est libérée. Dans les versions Debug, un échec d’assertion se produit si la liste est vide.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

Appelez cette méthode pour supprimer l’élément à la fin de la liste.

```cpp
E RemoveTail();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’élément à la fin de la liste.

### <a name="remarks"></a>Notes

L’élément de fin est supprimé de la liste et la mémoire est libérée. Une copie de l’élément est retournée. Dans les versions Debug, un échec d’assertion se produit si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

Appelez cette méthode pour supprimer l’élément à la fin de la liste sans retourner de valeur.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Notes

L’élément de fin est supprimé de la liste et la mémoire est libérée. Dans les versions Debug, un échec d’assertion se produit si la liste est vide.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlList :: IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList :: SetAt

Appelez cette méthode pour définir la valeur de l’élément à une position donnée dans la liste.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*imprim*<br/>
Valeur de POSITION correspondant à l’élément à modifier.

*appartient*<br/>
Nouvelle valeur de l’élément.

### <a name="remarks"></a>Notes

Remplace la valeur existante par l' *élément*. Dans les versions Debug, un échec d’assertion se produit si *pos* est égal à null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

Appelez cette méthode pour échanger des éléments dans la liste.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Paramètres

*pos1*<br/>
Valeur de la première POSITION.

*pos2*<br/>
Valeur de la deuxième POSITION.

### <a name="remarks"></a>Notes

Permute les éléments aux deux positions spécifiées. Dans les versions Debug, un échec d’assertion se produit si l’une des valeurs position est égale à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Voir aussi

[CList (classe)](../../mfc/reference/clist-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
