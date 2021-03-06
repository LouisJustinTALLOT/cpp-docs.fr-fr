---
description: 'En savoir plus sur : classeurs d’assistance de classe de collection'
title: Programmes d’assistance pour les classes de collection
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 9d3838ba0ba05441debb183e47d7df4e39229742
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331389"
---
# <a name="collection-class-helpers"></a>Programmes d’assistance pour les classes de collection

Les classes `CMap` de collection, `CList` et `CArray` utilisent des fonctions d’assistance globales basées sur des modèles à des fins telles que la comparaison, la copie et la sérialisation d’éléments. Dans le cadre de votre implémentation de classes basées sur `CMap` , `CList` et `CArray` , vous devez remplacer ces fonctions si nécessaire par des versions adaptées au type de données stockées dans votre mappage, votre liste ou votre tableau. Pour plus d’informations sur la substitution des fonctions d’assistance telles que `SerializeElements` , consultez l’article [Collections : comment créer un Type-Safe collection](../../mfc/how-to-make-a-type-safe-collection.md). Notez que `ConstructElements` et `DestructElements` ont été dépréciés.

L’bibliothèque MFC (Microsoft Foundation Class) fournit les fonctions globales suivantes dans afxtempl. h pour vous aider à personnaliser vos classes de collection :

### <a name="collection-class-helpers"></a>Programmes d’assistance pour les classes de collection

|Nom|Description|
|-|-|
|[CompareElements](#compareelements)|Indique si les éléments sont identiques.|
|[CopyElements](#copyelements)|Copie les éléments d’un tableau à un autre.|
|[DumpElements](#dumpelements)|Fournit une sortie de diagnostic orienté flux.|
|[HashKey](#hashkey)|Calcule une clé de hachage.|
|[SerializeElements](#serializeelements)|Stocke ou récupère des éléments dans une archive.|

## <a name="compareelements"></a><a name="compareelements"></a> CompareElements

Appelé directement par [CList :: find] (CList-Class. MD # not_found. MD # clist__find et indirectement par [cmap__lookup](cmap-class.md#lookup) et [cmap__operator &#91;&#93;](cmap-class.md#operator_at).

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Type du premier élément à comparer.

*pElement1*<br/>
Pointeur vers le premier élément à comparer.

*ARG_TYPE*<br/>
Type du deuxième élément à comparer.

*pElement2*<br/>
Pointeur vers le deuxième élément à comparer.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet pointé par *pElement1* est égal à l’objet pointé par *pElement2*; Sinon, 0.

### <a name="remarks"></a>Notes

Les `CMap` appels utilisent la `CMap` *clé* des paramètres de modèle et *ARG_KEY*.

L’implémentation par défaut retourne le résultat de la comparaison de *\* pElement1* et *\* pElement2*. Substituez cette fonction afin qu’elle compare les éléments d’une manière appropriée pour votre application.

Le langage C++ définit l’opérateur de comparaison ( `==` ) pour les types simples ( **`char`** , **`int`** , **`float`** , etc.), mais ne définit pas un opérateur de comparaison pour les classes et les structures. Si vous souhaitez utiliser `CompareElements` ou pour instancier l’une des classes de collection qui l’utilise, vous devez définir l’opérateur de comparaison ou la surcharge `CompareElements` avec une version qui retourne les valeurs appropriées.

### <a name="requirements"></a>Spécifications

   **En-tête :** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a> CopyElements

Cette fonction est appelée directement par [CArray :: Append](carray-class.md#append) et [CArray :: Copy](carray-class.md#copy).

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type d’éléments à copier.

*pDest*<br/>
Pointeur vers la destination dans laquelle les éléments sont copiés.

*pSrc*<br/>
Pointeur vers la source des éléments à copier.

*nCount*<br/>
Nombre d’éléments à copier.

### <a name="remarks"></a>Notes

L’implémentation par défaut utilise l’opérateur d’assignation simple ( **=** ) pour effectuer l’opération de copie. Si le type en cours de copie n’a pas d’opérateur surchargé =, l’implémentation par défaut effectue une copie au niveau du bit.

Pour plus d’informations sur l’implémentation de cette fonction et d’autres fonctions d’assistance, consultez l’article [Collections : comment créer un Type-Safe collection](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxtempl. h

## <a name="dumpelements"></a><a name="dumpelements"></a> DumpElements

Fournit une sortie de diagnostic orientée flux sous forme de texte pour les éléments de votre collection en cas de substitution.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*métafichier*<br/>
Contexte de vidage pour les éléments dump.

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments.

*papelements*<br/>
Pointeur vers les éléments à vider.

*nCount*<br/>
Nombre d’éléments à vider.

### <a name="remarks"></a>Notes

Les `CArray::Dump` `CList::Dump` fonctions, et `CMap::Dump` appellent This si la profondeur du dump est supérieure à 0.

L'implémentation par défaut n'exécute aucune opération. Si les éléments de votre collection sont dérivés de `CObject` , votre substitution effectue généralement une itération au sein des éléments de la collection, `Dump` en appelant pour chaque élément à son tour.

### <a name="requirements"></a>Spécifications

  **En-tête** afxtempl. h

## <a name="hashkey"></a><a name="hashkey"></a> HashKey

Calcule une valeur de hachage pour la clé donnée.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle qui spécifie le type de données utilisé pour accéder aux clés de carte.

*key*<br/>
Clé dont la valeur de hachage doit être calculée.

### <a name="return-value"></a>Valeur renvoyée

Valeur de hachage de la clé.

### <a name="remarks"></a>Notes

Cette fonction est appelée directement par [CMAP :: RemoveKey](cmap-class.md#removekey) et indirectement par [CMAP :: Lookup](cmap-class.md#lookup) et [CMAP :: Operator &#91;&#93;](cmap-class.md#operator_at).

L’implémentation par défaut crée une valeur de hachage en décalant la *clé* vers la droite de quatre positions. Substituez cette fonction afin qu’elle retourne des valeurs de hachage appropriées pour votre application.

### <a name="example"></a>Exemple

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>Spécifications

  **En-tête** afxtempl. h

## <a name="serializeelements"></a><a name="serializeelements"></a> SerializeElements

[CArray](carray-class.md), [CList](clist-class.md)et [CMAP](cmap-class.md) appellent cette fonction pour sérialiser des éléments.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments.

*ar*<br/>
Objet archive dans lequel effectuer l’archivage.

*papelements*<br/>
Pointeur vers les éléments en cours d’archivage.

*nCount*<br/>
Nombre d’éléments en cours d’archivage

### <a name="remarks"></a>Notes

L’implémentation par défaut effectue une opération de lecture ou d’écriture au niveau du bit.

Pour plus d’informations sur l’implémentation de cette fonction et d’autres fonctions d’assistance, consultez l’article [Collections : comment créer un Type-Safe collection](../how-to-make-a-type-safe-collection.md).

### <a name="example"></a>Exemple

Consultez l’exemple dans l’article [Collections : comment créer un Type-Safe collection](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxtempl. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CMap, classe](cmap-class.md)<br/>
[CList (classe)](clist-class.md)<br/>
[CArray (classe)](carray-class.md)
