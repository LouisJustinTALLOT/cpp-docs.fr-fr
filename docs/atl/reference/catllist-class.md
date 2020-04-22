---
title: Classe CAtlList
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
ms.openlocfilehash: 0e4ea8eef51431c100f5d3119d7f75e9673e276e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748740"
---
# <a name="catllist-class"></a>Classe CAtlList

Cette classe fournit des méthodes pour créer et gérer un objet de liste.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>Paramètres

*E*<br/>
Type de l’élément.

*ETraits (ETraits)*<br/>
Le code utilisé pour copier ou déplacer des éléments. Voir [CElementTraits Class](../../atl/reference/celementtraits-class.md) pour plus de détails.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|Constructeur.|
|[CAtlList::CAtlList](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|Appelez cette méthode pour ajouter un élément à la tête de la liste.|
|[CAtlList::AddHeadList](#addheadlist)|Appelez cette méthode pour ajouter une liste existante à la tête de la liste.|
|[CAtlList::AddTail](#addtail)|Appelez cette méthode pour ajouter un élément à la queue de cette liste.|
|[CAtlList::AddTailList](#addtaillist)|Appelez cette méthode pour ajouter une liste existante à la queue de cette liste.|
|[CAtlList::AssertValid](#assertvalid)|Appelez cette méthode pour confirmer que la liste est valide.|
|[CAtlList::Trouver](#find)|Appelez cette méthode pour rechercher la liste pour l’élément spécifié.|
|[CAtlList::FindIndex](#findindex)|Appelez cette méthode pour obtenir la position d’un élément, compte tenu d’une valeur indicative.|
|[CAtlList::GetAt](#getat)|Appelez cette méthode pour retourner l’élément à une position spécifiée dans la liste.|
|[CAtlList::GetCount](#getcount)|Appelez cette méthode pour retourner le nombre d’objets dans la liste.|
|[CAtlList::GetHead](#gethead)|Appelez cette méthode pour retourner l’élément en tête de liste.|
|[CAtlList::GetHeadPosition](#getheadposition)|Appelez cette méthode pour obtenir la position de la tête de liste.|
|[CAtlList::GetNext](#getnext)|Appelez cette méthode pour retourner l’élément suivant de la liste.|
|[CAtlList::GetPrev](#getprev)|Appelez cette méthode pour renvoyer l’élément précédent de la liste.|
|[CAtlList::GetTail](#gettail)|Appelez cette méthode pour retourner l’élément à la queue de la liste.|
|[CAtlList::GetTailPosition](#gettailposition)|Appelez cette méthode pour obtenir la position de la queue de la liste.|
|[CAtlList::InsertAfter](#insertafter)|Appelez cette méthode pour insérer un nouvel élément dans la liste après la position spécifiée.|
|[CAtlList::InsertBefore](#insertbefore)|Appelez cette méthode pour insérer un nouvel élément dans la liste avant la position spécifiée.|
|[CAtlList:IsEmpty](#isempty)|Appelez cette méthode pour déterminer si la liste est vide.|
|[CAtlList::MoveToHead](#movetohead)|Appelez cette méthode pour déplacer l’élément spécifié à la tête de la liste.|
|[CAtlList::MoveToTail](#movetotail)|Appelez cette méthode pour déplacer l’élément spécifié à la queue de la liste.|
|[CAtlList::RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments de la liste.|
|[CAtlList::RemoveAt](#removeat)|Appelez cette méthode pour supprimer un seul élément de la liste.|
|[CAtlList::RemoveHead](#removehead)|Appelez cette méthode pour supprimer l’élément en tête de liste.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Appelez cette méthode pour supprimer l’élément en tête de liste sans retourner une valeur.|
|[CAtlList::RemoveTail](#removetail)|Appelez cette méthode pour supprimer l’élément à la queue de la liste.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Appelez cette méthode pour supprimer l’élément à la queue de la liste sans retourner une valeur.|
|[CAtlList::SetAt](#setat)|Appelez cette méthode pour définir la valeur de l’élément à une position donnée dans la liste.|
|[CAtlList::SwapElements](#swapelements)|Appelez cette méthode pour échanger des éléments dans la liste.|

## <a name="remarks"></a>Notes

La `CAtlList` classe prend en charge les listes d’objets non syndiqués accessibles séquentiellement ou par valeur. `CAtlList`les listes se comportent comme des listes doublement liées. Chaque liste a une tête et une queue, et de nouveaux éléments (ou des listes dans certains cas) peuvent être ajoutés à l’une ou l’autre extrémité de la liste, ou insérés avant ou après des éléments spécifiques.

La plupart `CAtlList` des méthodes utilisent une valeur de position. Cette valeur est utilisée par les méthodes pour référencer l’emplacement de mémoire réel où les éléments sont stockés, et ne doit pas être calculé ou prédit directement. S’il est nécessaire d’accéder à *l’élément n*th dans la liste, la méthode [CAtlList::FindIndex](#findindex) retournera la valeur de position correspondante pour un indice donné. Les méthodes [CAtlList::GetNext](#getnext) et [CAtlList::GetPrev](#getprev) peut être utilisé pour itérer à travers les objets de la liste.

Pour plus d’informations sur les cours de collecte disponibles avec ATL, voir [cours de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead

Appelez cette méthode pour ajouter un élément à la tête de la liste.

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*Élément*<br/>
Nouvel élément.

### <a name="return-value"></a>Valeur de retour

Retourne la position de l’élément nouvellement ajouté.

### <a name="remarks"></a>Notes

Si la première version est utilisée, un élément vide est créé en utilisant son constructeur par défaut, plutôt que son constructeur de copie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

Appelez cette méthode pour ajouter une liste existante à la tête de la liste.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Paramètres

*plNous*<br/>
Liste à ajouter.

### <a name="remarks"></a>Notes

La liste indiquée par *plNew* est insérée au début de la liste existante. Dans les constructions de débog, une défaillance d’affirmation se produira si *plNew* est égal à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList::AddTail

Appelez cette méthode pour ajouter un élément à la queue de cette liste.

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*Élément*<br/>
Élément à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne le POSITION de l’élément nouvellement ajouté.

### <a name="remarks"></a>Notes

Si la première version est utilisée, un élément vide est créé en utilisant son constructeur par défaut, plutôt que son constructeur de copie. L’élément est ajouté à la fin de la liste, et il devient maintenant la queue. Cette méthode peut être utilisée avec une liste vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

Appelez cette méthode pour ajouter une liste existante à la queue de cette liste.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Paramètres

*plNous*<br/>
Liste à ajouter.

### <a name="remarks"></a>Notes

La liste indiquée par *plNew* est insérée après le dernier élément (le cas échéant) dans l’objet de liste. Le dernier élément de la liste *plNew* devient donc la queue. Dans les constructions de débog, une défaillance d’affirmation se produira si *plNew* est égal à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid

Appelez cette méthode pour confirmer que la liste est valide.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Notes

Dans les constructions de débog, une défaillance d’affirmation se produira si l’objet de liste n’est pas valide. Pour être valide, une liste vide doit avoir à la fois la tête et la queue pointant vers NULL, et une liste qui n’est pas vide doit avoir à la fois la tête et la queue pointant vers les adresses valides.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

Constructeur.

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

Le constructeur de `CAtlList` l’objet. La taille du bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est nécessaire. De plus grandes tailles de blocs réduisent les appels aux routines d’allocation de mémoire, mais utilisent plus de ressources.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList::CAtlList

Destructeur.

```
~CAtlList() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, y compris un appel à [CAtlList::RemoveAll](#removeall) pour supprimer tous les éléments de la liste.

Dans les constructions de débog, une défaillance d’affirmation se `RemoveAll`produira si la liste contient encore quelques éléments après l’appel à .

## <a name="catllistfind"></a><a name="find"></a>CAtlList::Trouver

Appelez cette méthode pour rechercher la liste pour l’élément spécifié.

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*Élément*<br/>
L’élément à trouver dans la liste.

*posStartAprès*<br/>
La position de départ pour la recherche. Si aucune valeur n’est spécifiée, la recherche commence par l’élément de tête.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur POSITION de l’élément si elle est trouvée, sinon retourne NULL.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une défaillance d’affirmation se produira si l’objet de liste n’est pas valide, ou si la valeur *posStartAfter* est hors de portée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList::FindIndex

Appelez cette méthode pour obtenir la position d’un élément, compte tenu d’une valeur indicative.

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Paramètres

*iElement (en)*<br/>
L’indice zéro de l’élément de liste requis.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur POSITION correspondante, ou NULL si *iElement* est hors de portée.

### <a name="remarks"></a>Notes

Cette méthode renvoie le POSITION correspondant à une valeur indiciel donnée, permettant l’accès à *l’élément n*e de la liste.

Dans les constructions de débog, une défaillance d’affirmation se produira si l’objet de liste n’est pas valide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList::GetAt

Appelez cette méthode pour retourner l’élément à une position spécifiée dans la liste.

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
La valeur POSITION spécifiant un élément particulier.

### <a name="return-value"></a>Valeur de retour

Une référence à l’élément ou une copie de celui-là.

### <a name="remarks"></a>Notes

Si la liste est `GetAt` **const**, renvoie une copie de l’élément. Cela permet à la méthode d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège la liste contre la modification.

Si la liste **n’est**pas const , `GetAt` renvoie une référence à l’élément. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

Dans les constructions de débog, une défaillance d’affirmation se produira si *pos* est égal à NULL.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:FindIndex](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList::GetCount

Appelez cette méthode pour retourner le nombre d’objets dans la liste.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d'éléments figurant dans la liste.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:Find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead

Appelez cette méthode pour retourner l’élément en tête de liste.

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie une référence ou une copie de l’élément à la tête de la liste.

### <a name="remarks"></a>Notes

Si la liste est `GetHead` **const**, renvoie une copie de l’élément à la tête de la liste. Cela permet à la méthode d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège la liste contre la modification.

Si la liste **n’est**pas const , `GetHead` renvoie une référence à l’élément en tête de liste. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

Dans les constructions de débog, une défaillance d’affirmation se produira si le chef de la liste pointe vers NULL.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:AddHead](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

Appelez cette méthode pour obtenir la position de la tête de liste.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur POSITION correspondant à l’élément en tête de liste.

### <a name="remarks"></a>Notes

Si la liste est vide, la valeur retournée est NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList::GetNext

Appelez cette méthode pour retourner l’élément suivant de la liste.

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Une valeur POSITION, retournée par `GetNext`un appel précédent à , [CAtlList::GetHeadPosition](#getheadposition), ou une autre `CAtlList` méthode.

### <a name="return-value"></a>Valeur de retour

Si la liste est `GetNext` **const**, renvoie une copie de l’élément suivant de la liste. Cela permet à la méthode d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège la liste contre la modification.

Si la liste **n’est**pas const , `GetNext` renvoie une référence à l’élément suivant de la liste. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Le compteur POSITION, *pos*, est mis à jour pour indiquer l’élément suivant dans la liste, ou NULL s’il n’y a plus d’éléments. Dans les constructions de débog, une défaillance d’affirmation se produira si *pos* est égal à NULL.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev

Appelez cette méthode pour renvoyer l’élément précédent de la liste.

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Une valeur POSITION, retournée par `GetPrev`un appel précédent à , [CAtlList::GetTailPosition](#gettailposition), ou une autre `CAtlList` méthode.

### <a name="return-value"></a>Valeur de retour

Si la liste est `GetPrev` **const**, renvoie une copie d’un élément de la liste. Cela permet à la méthode d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège la liste contre la modification.

Si la liste **n’est**pas const , `GetPrev` renvoie une référence à un élément de la liste. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Le compteur POSITION, *pos*, est mis à jour pour indiquer l’élément précédent dans la liste, ou NULL s’il n’y a plus d’éléments. Dans les constructions de débog, une défaillance d’affirmation se produira si *pos* est égal à NULL.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail

Appelez cette méthode pour retourner l’élément à la queue de la liste.

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie une référence ou une copie de l’élément à la queue de la liste.

### <a name="remarks"></a>Notes

Si la liste est `GetTail` **const**, renvoie une copie de l’élément à la tête de la liste. Cela permet à la méthode d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège la liste contre la modification.

Si la liste **n’est**pas const , `GetTail` renvoie une référence à l’élément en tête de liste. Cela permet d’utiliser la méthode de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

Dans les constructions de débog, une défaillance d’affirmation se produira si la queue de la liste pointe vers NULL.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:AddTail](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

Appelez cette méthode pour obtenir la position de la queue de la liste.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur POSITION correspondant à l’élément à la queue de la liste.

### <a name="remarks"></a>Notes

Si la liste est vide, la valeur retournée est NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

Type utilisé lorsqu’un élément est adopté comme argument d’entrée.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList::InsertAfter

Appelez cette méthode pour insérer un nouvel élément dans la liste après la position spécifiée.

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
La valeur POSITION après laquelle le nouvel élément sera inséré.

*Élément*<br/>
L’élément à insérer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur POSITION du nouvel élément.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une défaillance d’affirmation se produira si la liste n’est pas valide, si l’insert échoue, ou si une tentative est faite pour insérer l’élément après la queue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList::InsertBefore

Appelez cette méthode pour insérer un nouvel élément dans la liste avant la position spécifiée.

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le nouvel élément sera inséré dans la liste avant cette valeur POSITION.

*Élément*<br/>
L’élément à insérer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur POSITION du nouvel élément.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une défaillance d’affirmation se produira si la liste n’est pas valide, si l’insert échoue, ou si une tentative est faite pour insérer l’élément avant la tête.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList:IsEmpty

Appelez cette méthode pour déterminer si la liste est vide.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si la liste ne contient pas d’objets, sinon faux.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

Appelez cette méthode pour déplacer l’élément spécifié à la tête de la liste.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
La valeur POSITION de l’élément à déplacer.

### <a name="remarks"></a>Notes

L’élément spécifié est déplacé de sa position actuelle à la tête de la liste. Dans les constructions de débog, une défaillance d’affirmation se produira si *pos* est égal à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

Appelez cette méthode pour déplacer l’élément spécifié à la queue de la liste.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
La valeur POSITION de l’élément à déplacer.

### <a name="remarks"></a>Notes

L’élément spécifié est déplacé de sa position actuelle à la queue de la liste. Dans les constructions de débog, une défaillance d’affirmation se produira si *pos* est égal à NULL.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList::RemoveAll

Appelez cette méthode pour supprimer tous les éléments de la liste.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Cette méthode supprime tous les éléments de la liste et libère la mémoire allouée. Dans les constructions de débogots, un ATLASSERT sera soulevé si tous les éléments ne sont pas supprimés ou si la structure de liste est devenue corrompue.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList::RemoveAt

Appelez cette méthode pour supprimer un seul élément de la liste.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
La valeur POSITION de l’élément à supprimer.

### <a name="remarks"></a>Notes

L’élément référencé par *pos* est supprimé, et la mémoire est libérée. Il est acceptable `RemoveAt` d’utiliser pour enlever la tête ou la queue de la liste.

Dans les constructions de débog, une défaillance d’affirmation se produira si la liste n’est pas valide ou si la suppression de l’élément provoque la liste d’accéder à la mémoire qui ne fait pas partie de la structure de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

Appelez cette méthode pour supprimer l’élément en tête de liste.

```
E RemoveHead();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’élément en tête de liste.

### <a name="remarks"></a>Notes

L’élément de tête est supprimé de la liste, et la mémoire est libérée. Une copie de l’élément est retournée. Dans les constructions de débog, une défaillance d’affirmation se produira si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

Appelez cette méthode pour supprimer l’élément en tête de liste sans retourner une valeur.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Notes

L’élément de tête est supprimé de la liste, et la mémoire est libérée. Dans les constructions de débog, une défaillance d’affirmation se produira si la liste est vide.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

Appelez cette méthode pour supprimer l’élément à la queue de la liste.

```
E RemoveTail();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’élément à la queue de la liste.

### <a name="remarks"></a>Notes

L’élément de queue est supprimé de la liste, et la mémoire est libérée. Une copie de l’élément est retournée. Dans les constructions de débog, une défaillance d’affirmation se produira si la liste est vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

Appelez cette méthode pour supprimer l’élément à la queue de la liste sans retourner une valeur.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Notes

L’élément de queue est supprimé de la liste, et la mémoire est libérée. Dans les constructions de débog, une défaillance d’affirmation se produira si la liste est vide.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlList:IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList::SetAt

Appelez cette méthode pour définir la valeur de l’élément à une position donnée dans la liste.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
La valeur POSITION correspondant à l’élément à modifier.

*Élément*<br/>
La nouvelle valeur d’élément.

### <a name="remarks"></a>Notes

Remplace la valeur existante par *un élément*. Dans les constructions de débog, une défaillance d’affirmation se produira si *pos* est égal à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

Appelez cette méthode pour échanger des éléments dans la liste.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Paramètres

*pos1*<br/>
La première valeur POSITION.

*pos2*<br/>
La deuxième valeur POSITION.

### <a name="remarks"></a>Notes

Échange les éléments aux deux positions spécifiées. Dans les constructions de débog, une défaillance d’affirmation se produira si l’une ou l’autre valeur de position est égale à NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Voir aussi

[CList, classe](../../mfc/reference/clist-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
