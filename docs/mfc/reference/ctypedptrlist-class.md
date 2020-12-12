---
description: 'En savoir plus sur : classe CTypedPtrList'
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
ms.openlocfilehash: 353e9af00b1366b260ce3cb3689018a8e4e370c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318531"
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
Classe de base de la classe de liste de pointeurs typés ; doit être une classe de liste de pointeurs ( `CObList` ou `CPtrList` ).

*TYPE*<br/>
Type des éléments stockés dans la liste de classes de base.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTypedPtrList :: AddHead](#addhead)|Ajoute un élément (ou tous les éléments d’une autre liste) au début de la liste (crée un nouvel en-tête).|
|[CTypedPtrList :: AddTail](#addtail)|Ajoute un élément (ou tous les éléments d’une autre liste) à la fin de la liste (crée une nouvelle fin).|
|[CTypedPtrList :: GetAt](#getat)|Obtient l’élément à une position donnée.|
|[CTypedPtrList :: GetHead](#gethead)|Retourne l’élément head de la liste (ne peut pas être vide).|
|[CTypedPtrList :: GetNext](#getnext)|Obtient l’élément suivant pour l’itération.|
|[CTypedPtrList :: GetPrev](#getprev)|Obtient l’élément précédent pour l’itération.|
|[CTypedPtrList :: GetTail](#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|
|[CTypedPtrList :: RemoveHead](#removehead)|Supprime l’élément du début de la liste.|
|[CTypedPtrList :: RemoveTail](#removetail)|Supprime l’élément de la fin de la liste.|
|[CTypedPtrList :: SetAt](#setat)|Définit l’élément à une position donnée.|

## <a name="remarks"></a>Notes

Lorsque vous utilisez `CTypedPtrList` plutôt que `CObList` ou `CPtrList` , la fonctionnalité de contrôle de type C++ permet d’éliminer les erreurs provoquées par des types pointeur incompatibles.

En outre, le `CTypedPtrList` Wrapper effectue une grande partie du cast qui serait nécessaire si vous utilisiez `CObList` ou `CPtrList` .

Étant donné que toutes les `CTypedPtrList` fonctions sont Inline, l’utilisation de ce modèle n’affecte pas de manière significative la taille ou la vitesse de votre code.

Les listes dérivées de `CObList` peuvent être sérialisées, mais celles dérivées de `CPtrList` ne peuvent pas.

Lorsqu’un `CTypedPtrList` objet est supprimé ou que ses éléments sont supprimés, seuls les pointeurs sont supprimés, et non les entités auxquelles ils font référence.

Pour plus d’informations sur l’utilisation de `CTypedPtrList` , consultez les articles [Collections](../../mfc/collections.md) et [classes basées sur des modèles](../../mfc/template-based-classes.md).

## <a name="example"></a>Exemple

Cet exemple crée une instance de `CTypedPtrList` , ajoute un objet, sérialise la liste sur le disque, puis supprime l’objet :

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a> CTypedPtrList :: AddHead

Cette fonction membre appelle `BASE_CLASS` **:: AddHead**.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Type des éléments stockés dans la liste de classes de base.

*newElement*<br/>
Pointeur d’objet à ajouter à cette liste. Une valeur NULL est autorisée.

*BASE_CLASS*<br/>
Classe de base de la classe de liste de pointeurs typés ; doit être une classe de liste de pointeurs ( [CObList](../../mfc/reference/coblist-class.md) ou [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Pointeur vers un autre objet [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) . Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur renvoyée

La première version retourne la valeur de POSITION de l’élément qui vient d’être inséré.

### <a name="remarks"></a>Notes

La première version ajoute un nouvel élément avant le début de la liste. La deuxième version ajoute une autre liste d’éléments avant le début.

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a> CTypedPtrList :: AddTail

Cette fonction membre appelle `BASE_CLASS` **:: AddTail**.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Type des éléments stockés dans la liste de classes de base.

*newElement*<br/>
Pointeur d’objet à ajouter à cette liste. Une valeur NULL est autorisée.

*BASE_CLASS*<br/>
Classe de base de la classe de liste de pointeurs typés ; doit être une classe de liste de pointeurs ( [CObList](../../mfc/reference/coblist-class.md) ou [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Pointeur vers un autre objet [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) . Les éléments de *pNewList* seront ajoutés à cette liste.

### <a name="return-value"></a>Valeur renvoyée

La première version retourne la valeur de POSITION de l’élément qui vient d’être inséré.

### <a name="remarks"></a>Notes

La première version ajoute un nouvel élément après la fin de la liste. La deuxième version ajoute une autre liste d’éléments après la fin de la liste.

## <a name="ctypedptrlistgetat"></a><a name="getat"></a> CTypedPtrList :: GetAt

Une variable de type POSITION est une clé pour la liste.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.

*position*<br/>
Valeur de POSITION retournée par un `GetHeadPosition` `Find` appel de fonction membre ou précédent.

### <a name="return-value"></a>Valeur renvoyée

Si la liste est accessible via un pointeur vers `const CTypedPtrList` , `GetAt` retourne un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger ainsi la liste contre toute modification.

Si la liste est accessible directement ou via un pointeur vers `CTypedPtrList` , `GetAt` retourne une référence à un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Ce n’est pas le même qu’un index, et vous ne pouvez pas utiliser une valeur POSITION vous-même. `GetAt` Récupère le `CObject` pointeur associé à une position donnée.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Cette fonction inline appelle `BASE_CLASS` **:: GetAt**.

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a> CTypedPtrList :: GetHead

Obtient le pointeur qui représente l’élément head de cette liste.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.

### <a name="return-value"></a>Valeur renvoyée

Si la liste est accessible via un pointeur vers `const CTypedPtrList` , `GetHead` retourne un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger ainsi la liste contre toute modification.

Si la liste est accessible directement ou via un pointeur vers `CTypedPtrList` , `GetHead` retourne une référence à un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetHead` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a> CTypedPtrList :: GetNext

Obtient l’élément de liste identifié par *rPosition*, puis affecte à *rPosition* la valeur de position de l’entrée suivante dans la liste.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type d’éléments contenus dans cette liste.

*rPosition*<br/>
Référence à une valeur de POSITION retournée par un `GetNext` `GetHeadPosition` appel de fonction membre précédent, ou autre.

### <a name="return-value"></a>Valeur renvoyée

Si la liste est accessible via un pointeur vers `const CTypedPtrList` , `GetNext` retourne un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger ainsi la liste contre toute modification.

Si la liste est accessible directement ou via un pointeur vers `CTypedPtrList` , `GetNext` retourne une référence à un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetNext` dans une boucle d’itération directe si vous établissez la position initiale avec un appel à `GetHeadPosition` ou [CPtrList :: find](../../mfc/reference/coblist-class.md#find).

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Si l’élément récupéré est le dernier de la liste, la nouvelle valeur de *rPosition* est définie sur null.

Il est possible de supprimer un élément pendant une itération. Consultez l’exemple pour [CObList :: RemoveAt](../../mfc/reference/coblist-class.md#removeat).

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a> CTypedPtrList :: GetPrev

Obtient l’élément de liste identifié par *rPosition*, puis affecte à *rPosition* la valeur de position de l’entrée précédente dans la liste.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type d’éléments contenus dans cette liste.

*rPosition*<br/>
Référence à une valeur de POSITION retournée par un `GetPrev` appel de fonction membre ou précédent.

### <a name="return-value"></a>Valeur renvoyée

Si la liste est accessible via un pointeur vers `const CTypedPtrList` , `GetPrev` retourne un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger ainsi la liste contre toute modification.

Si la liste est accessible directement ou via un pointeur vers `CTypedPtrList` , `GetPrev` retourne une référence à un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous pouvez utiliser `GetPrev` dans une boucle d’itération inverse si vous établissez la position initiale avec un appel à `GetTailPosition` ou `Find` .

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Si l’élément récupéré est le premier de la liste, la nouvelle valeur de *rPosition* est définie sur null.

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a> CTypedPtrList :: GetTail

Obtient le pointeur qui représente l’élément head de cette liste.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.

### <a name="return-value"></a>Valeur renvoyée

Si la liste est accessible via un pointeur vers `const CTypedPtrList` , `GetTail` retourne un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction uniquement sur le côté droit d’une instruction d’assignation et de protéger ainsi la liste contre toute modification.

Si la liste est accessible directement ou via un pointeur vers `CTypedPtrList` , `GetTail` retourne une référence à un pointeur du type spécifié par le *type* de paramètre de modèle. Cela permet d’utiliser la fonction de chaque côté d’une instruction d’assignation, ce qui permet de modifier les entrées de liste.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetTail` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a> CTypedPtrList :: RemoveHead

Supprime l’élément de l’en-tête de la liste et le retourne.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.

### <a name="return-value"></a>Valeur renvoyée

Pointeur précédemment à l’en-tête de la liste. Ce pointeur est du type spécifié par le *type* de paramètre de modèle.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveHead` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a> CTypedPtrList :: RemoveTail

Supprime l’élément de la fin de la liste et le retourne.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.

### <a name="return-value"></a>Valeur renvoyée

Pointeur précédemment à la fin de la liste. Ce pointeur est du type spécifié par le *type* de paramètre de modèle.

### <a name="remarks"></a>Notes

Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveTail` . Si la liste est vide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.

## <a name="ctypedptrlistsetat"></a><a name="setat"></a> CTypedPtrList :: SetAt

Cette fonction membre appelle `BASE_CLASS` **:: setat**.

```cpp
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
POSITION de l’élément à définir.

*TYPE*<br/>
Type des éléments stockés dans la liste de classes de base.

*newElement*<br/>
Pointeur d’objet à écrire dans la liste.

### <a name="remarks"></a>Notes

Une variable de type POSITION est une clé pour la liste. Ce n’est pas le même qu’un index, et vous ne pouvez pas utiliser une valeur POSITION vous-même. `SetAt` écrit le pointeur d’objet à la position spécifiée dans la liste.

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

Pour obtenir des remarques plus détaillées, consultez [CObList :: setat](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPtrList, classe](../../mfc/reference/cptrlist-class.md)<br/>
[CObList (classe)](../../mfc/reference/coblist-class.md)
