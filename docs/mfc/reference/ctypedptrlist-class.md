---
title: CTypedPtrList, classe
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 40dbfb822e71309e9675aba14d46d333ffa4ee06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373263"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList, classe

Fournit un « wrapper » de type sécurisé pour les objets de la classe `CPtrList`.

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de liste de pointeurs dactylographie; doit être une classe `CObList` `CPtrList`de liste de pointeurs ( ou ).

*TYPE*<br/>
Type des éléments stockés dans la liste de la classe de base.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|Ajoute un élément (ou tous les éléments d’une autre liste) à la tête de la liste (fait une nouvelle tête).|
|[CTypedPtrList::AddTail](#addtail)|Ajoute un élément (ou tous les éléments d’une autre liste) à la queue de la liste (fait une nouvelle queue).|
|[CTypedPtrList::GetAt](#getat)|Obtient l’élément à une position donnée.|
|[CTypedPtrList::GetHead](#gethead)|Retourne l’élément tête de la liste (ne peut pas être vide).|
|[CTypedPtrList::GetNext](#getnext)|Obtient le prochain élément pour itérer.|
|[CTypedPtrList::GetPrev](#getprev)|Obtient l’élément précédent pour itérer.|
|[CTypedPtrList::GetTail](#gettail)|Retourne l’élément de queue de la liste (ne peut pas être vide).|
|[CTypedPtrList::RemoveHead](#removehead)|Supprime l’élément de la tête de liste.|
|[CTypedPtrList::RemoveTail](#removetail)|Supprime l’élément de la queue de la liste.|
|[CTypedPtrList::SetAt](#setat)|Définit l’élément à une position donnée.|

## <a name="remarks"></a>Notes

Lorsque vous `CTypedPtrList` utilisez `CObList` `CPtrList`plutôt que ou, l’installation de vérification de type CMD aide à éliminer les erreurs causées par des types de pointeurs dépareillés.

En outre, `CTypedPtrList` l’emballage effectue une grande partie de `CObList` la `CPtrList`coulée qui serait nécessaire si vous avez utilisé ou .

Étant `CTypedPtrList` donné que toutes les fonctions sont inlines, l’utilisation de ce modèle n’affecte pas de manière significative la taille ou la vitesse de votre code.

Les listes `CObList` dérivées peuvent être sérialisées, mais celles dérivées de `CPtrList` ne peut pas.

Lorsqu’un `CTypedPtrList` objet est supprimé, ou lorsque ses éléments sont supprimés, seuls les pointeurs sont supprimés, et non les entités qu’ils renvoient.

Pour plus d’informations sur l’utilisation `CTypedPtrList`, voir les articles [Collections](../../mfc/collections.md) et [Template-Based Classes](../../mfc/template-based-classes.md).

## <a name="example"></a>Exemple

Cet exemple crée `CTypedPtrList`une instance de , ajoute un objet, sérialisse la liste au disque, puis supprime l’objet:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a>CTypedPtrList::AddHead

Cette fonction `BASE_CLASS`de membre appelle **::AddHead**.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Type des éléments stockés dans la liste de la classe de base.

*nouvel Element*<br/>
Le pointeur d’objet à ajouter à cette liste. Une valeur NULL est autorisée.

*BASE_CLASS*<br/>
Classe de base de la classe de liste de pointeurs dactylographie; doit être une classe de liste de pointeurs ( [CObList](../../mfc/reference/coblist-class.md) ou [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList (en)*<br/>
Un pointeur vers un autre objet [CTypedPtrList.](../../mfc/reference/ctypedptrlist-class.md) Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version renvoie la valeur POSITION de l’élément nouvellement inséré.

### <a name="remarks"></a>Notes

La première version ajoute un nouvel élément avant la tête de liste. La deuxième version ajoute une autre liste d’éléments avant la tête.

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a>CTypedPtrList::AddTail

Cette fonction `BASE_CLASS`de membre appelle **::AddTail**.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Type des éléments stockés dans la liste de la classe de base.

*nouvel Element*<br/>
Le pointeur d’objet à ajouter à cette liste. Une valeur NULL est autorisée.

*BASE_CLASS*<br/>
Classe de base de la classe de liste de pointeurs dactylographie; doit être une classe de liste de pointeurs ( [CObList](../../mfc/reference/coblist-class.md) ou [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList (en)*<br/>
Un pointeur vers un autre objet [CTypedPtrList.](../../mfc/reference/ctypedptrlist-class.md) Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur de retour

La première version renvoie la valeur POSITION de l’élément nouvellement inséré.

### <a name="remarks"></a>Notes

La première version ajoute un nouvel élément après la queue de la liste. La deuxième version ajoute une autre liste d’éléments après la queue de la liste.

## <a name="ctypedptrlistgetat"></a><a name="getat"></a>CTypedPtrList::GetAt

Une variable de type POSITION est une clé pour la liste.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments stockés dans la liste.

*position*<br/>
Une valeur POSITION retournée `GetHeadPosition` `Find` par un appel de fonction préalable ou membre.

### <a name="return-value"></a>Valeur de retour

Si la liste est accessible par `const CTypedPtrList`un `GetAt` pointeur à un , puis retourne un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège ainsi la liste contre la modification.

Si la liste est consultée directement `CTypedPtrList`ou `GetAt` par l’intermédiaire d’un pointeur à un , puis retourne une référence à un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Ce n’est pas la même chose qu’un index, et vous ne pouvez pas fonctionner sur une valeur POSITION vous-même. `GetAt`récupère le `CObject` pointeur associé à une position donnée.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Cette fonction en `BASE_CLASS`ligne appelle **::GetAt**.

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a>CTypedPtrList::GetHead

Obtient le pointeur qui représente l’élément de tête de cette liste.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments stockés dans la liste.

### <a name="return-value"></a>Valeur de retour

Si la liste est accessible par `const CTypedPtrList`un `GetHead` pointeur à un , puis retourne un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège ainsi la liste contre la modification.

Si la liste est consultée directement `CTypedPtrList`ou `GetHead` par l’intermédiaire d’un pointeur à un , puis retourne une référence à un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `GetHead`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a>CTypedPtrList::GetNext

Obtient l’élément de liste identifié par *rPosition*, puis définit *rPosition* à la valeur POSITION de la prochaine entrée dans la liste.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments contenus dans cette liste.

*rPosition*<br/>
Une référence à une valeur `GetNext`POSITION `GetHeadPosition`retournée par un précédent , , ou un autre appel de fonction de membre.

### <a name="return-value"></a>Valeur de retour

Si la liste est accessible par `const CTypedPtrList`un `GetNext` pointeur à un , puis retourne un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège ainsi la liste contre la modification.

Si la liste est consultée directement `CTypedPtrList`ou `GetNext` par l’intermédiaire d’un pointeur à un , puis retourne une référence à un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous pouvez `GetNext` utiliser dans une boucle d’itération vers l’avant si vous établissez la position initiale avec un appel ou `GetHeadPosition` [CPtrList::Trouver](../../mfc/reference/coblist-class.md#find).

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Si l’élément récupéré est le dernier de la liste, alors la nouvelle valeur de *rPosition* est réglée à NULL.

Il est possible d’enlever un élément lors d’une itération. Voir l’exemple pour [CObList:RemoveAt](../../mfc/reference/coblist-class.md#removeat).

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a>CTypedPtrList::GetPrev

Obtient l’élément de liste identifié par *rPosition*, puis définit *rPosition* à la valeur POSITION de l’entrée précédente dans la liste.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments contenus dans cette liste.

*rPosition*<br/>
Une référence à une valeur `GetPrev` POSITION retournée par un appel de fonction de membre précédent ou autre.

### <a name="return-value"></a>Valeur de retour

Si la liste est accessible par `const CTypedPtrList`un `GetPrev` pointeur à un , puis retourne un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège ainsi la liste contre la modification.

Si la liste est consultée directement `CTypedPtrList`ou `GetPrev` par l’intermédiaire d’un pointeur à un , puis retourne une référence à un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous pouvez `GetPrev` utiliser dans une boucle d’itération inversée `GetTailPosition` si `Find`vous établissez la position initiale avec un appel à ou .

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Si l’élément récupéré est le premier de la liste, la nouvelle valeur de *la rPosition* est réglée sur NULL.

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a>CTypedPtrList::GetTail

Obtient le pointeur qui représente l’élément de tête de cette liste.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments stockés dans la liste.

### <a name="return-value"></a>Valeur de retour

Si la liste est accessible par `const CTypedPtrList`un `GetTail` pointeur à un , puis retourne un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet à la fonction d’être utilisée uniquement sur le côté droit d’une instruction d’affectation et protège ainsi la liste contre la modification.

Si la liste est consultée directement `CTypedPtrList`ou `GetTail` par l’intermédiaire d’un pointeur à un , puis retourne une référence à un pointeur du type spécifié par le paramètre type *TYPE*. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’affectation et permet ainsi de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `GetTail`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a>CTypedPtrList::RemoveHead

Supprime l’élément de la tête de liste et le renvoie.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments stockés dans la liste.

### <a name="return-value"></a>Valeur de retour

Le pointeur précédemment en tête de liste. Ce pointeur est du type spécifié par le paramètre type *TYPE*.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `RemoveHead`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a>CTypedPtrList::RemoveTail

Supprime l’élément de la queue de la liste et le renvoie.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments stockés dans la liste.

### <a name="return-value"></a>Valeur de retour

Le pointeur précédemment à la queue de la liste. Ce pointeur est du type spécifié par le paramètre type *TYPE*.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la `RemoveTail`liste n’est pas vide avant d’appeler . Si la liste est vide, la version Debug de la Microsoft Foundation Class Library affirme. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

## <a name="ctypedptrlistsetat"></a><a name="setat"></a>CTypedPtrList::SetAt

Cette fonction `BASE_CLASS`de membre appelle **::SetAt**.

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le POSITION de l’élément à définir.

*TYPE*<br/>
Type des éléments stockés dans la liste de la classe de base.

*nouvel Element*<br/>
Le pointeur d’objet à écrire sur la liste.

### <a name="remarks"></a>Notes

Une variable de type POSITION est une clé pour la liste. Ce n’est pas la même chose qu’un index, et vous ne pouvez pas fonctionner sur une valeur POSITION vous-même. `SetAt`écrit le pointeur d’objet à la position spécifiée dans la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

Pour des remarques plus détaillées, voir [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPtrList, classe](../../mfc/reference/cptrlist-class.md)<br/>
[CObList, classe](../../mfc/reference/coblist-class.md)
