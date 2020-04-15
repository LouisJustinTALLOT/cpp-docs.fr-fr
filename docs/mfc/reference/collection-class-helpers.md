---
title: Programmes d’assistance pour les classes de collection
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 05fe49a4d8e6de92c584d40f3871f3efb906c7c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374817"
---
# <a name="collection-class-helpers"></a>Programmes d’assistance pour les classes de collection

Les classes `CMap` `CList`de `CArray` collecte , , et l’utilisation des fonctions d’aide globale modélisées à des fins telles que la comparaison, la copie et la sérialisation des éléments. Dans le cadre de votre `CMap` `CList`mise `CArray`en œuvre de classes basées sur , , et , vous devez remplacer ces fonctions au besoin avec des versions adaptées au type de données stockées dans votre carte, liste, ou tableau. Pour plus d’informations sur les `SerializeElements`fonctions d’aide primordiale telles que , voir l’article [Collections: How to Make a Type-Safe Collection](../../mfc/how-to-make-a-type-safe-collection.md). Notez `ConstructElements` `DestructElements` cela et ont été dépréciés.

La Microsoft Foundation Class Library fournit les fonctions globales suivantes dans afxtempl.h pour vous aider à personnaliser vos classes de collection :

### <a name="collection-class-helpers"></a>Programmes d’assistance pour les classes de collection

|||
|-|-|
|[CompareElements](#compareelements)|Indique si les éléments sont les mêmes.|
|[CopyElements](#copyelements)|Copie des éléments d’un tableau à l’autre.|
|[DumpElements](#dumpelements)|Fournit des résultats diagnostiques axés sur le flux.|
|[HashKey (en)](#hashkey)|Calcule une clé de hachage.|
|[SerializeElements](#serializeelements)|Stocke ou récupère des éléments à partir ou à partir d’une archive.|

## <a name="compareelements"></a><a name="compareelements"></a>CompareElements

Appelé directement par [CList::Find] (clist-class.md-not_found.md-clist__find et indirectement par [cmap__lookup](cmap-class.md#lookup) et [cmap__operator &#91;&#93;](cmap-class.md#operator_at).

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Le type du premier élément à comparer.

*pElement1*<br/>
Pointeur sur le premier élément à comparer.

*ARG_TYPE*<br/>
Le type du deuxième élément à comparer.

*pElement2*<br/>
Pointeur sur le deuxième élément à comparer.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet pointé par *pElement1* est égal à l’objet pointé par *pElement2*; sinon 0.

### <a name="remarks"></a>Notes

Les `CMap` appels `CMap` utilisent les paramètres du modèle *KEY* et *ARG_KEY*.

La mise en œuvre par défaut renvoie le résultat de la comparaison de * \*pElement1* et * \*pElement2*. Remplacer cette fonction afin qu’elle compare les éléments d’une manière appropriée pour votre application.

La langue Cmd définit l’opérateur de `==`comparaison ( ) pour les types simples **(char**, **int**, **flotteur,** etc.) mais ne définit pas un opérateur de comparaison pour les classes et les structures. Si vous souhaitez `CompareElements` utiliser ou instantané l’une des classes de collecte qui l’utilise, vous devez soit définir l’opérateur de comparaison ou la surcharge `CompareElements` avec une version qui renvoie des valeurs appropriées.

### <a name="requirements"></a>Spécifications

   **En-tête :** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>CopyElements

Cette fonction est appelée directement par [CArray::Append](carray-class.md#append) et [CArray::Copy](carray-class.md#copy).

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments à copier.

*pDest*<br/>
Pointeur vers la destination où les éléments seront copiés.

*pSrc (en)*<br/>
Pointeur vers la source des éléments à copier.

*nCompte*<br/>
Nombre d’éléments à copier.

### <a name="remarks"></a>Notes

La mise en œuvre **=** par défaut utilise l’opérateur d’affectation simple ( ) pour effectuer l’opération de copie. Si le type copié n’a pas d’opérateur surchargé, la mise en œuvre par défaut effectue une copie un peu plus sage.

Pour plus d’informations sur la mise en œuvre de cette fonction et d’autres fonctions d’aide, consultez l’article [Collections: How to Make a Type-Safe Collection](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxtempl.h

## <a name="dumpelements"></a><a name="dumpelements"></a>DumpElements DumpElements

Fournit la sortie diagnostique axée sur le flux sous forme de texte pour les éléments de votre collection lorsqu’il est remplacé.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*Dc*<br/>
Contexte de vidange pour les éléments de dumping.

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments.

*pElements*<br/>
Pointeur sur les éléments à jeter.

*nCompte*<br/>
Nombre d’éléments à sous-erguer.

### <a name="remarks"></a>Notes

Le `CArray::Dump` `CList::Dump`, `CMap::Dump` , et les fonctions appellent ceci si la profondeur de la décharge est supérieure à 0.

L'implémentation par défaut n'exécute aucune opération. Si les éléments de votre `CObject`collection sont dérivés, votre remplacement s’ytira généralement à travers les éléments de la collection, appelant `Dump` à chaque élément à son tour.

### <a name="requirements"></a>Spécifications

  **En-tête** afxtempl.h

## <a name="hashkey"></a><a name="hashkey"></a>HashKey (en)

Calcule une valeur de hachage pour la clé donnée.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de données utilisé pour accéder aux clés de la carte.

*key*<br/>
La clé dont la valeur de hachage doit être calculée.

### <a name="return-value"></a>Valeur de retour

La valeur de hachage de la clé.

### <a name="remarks"></a>Notes

Cette fonction est appelée directement par [CMap::RemoveKey](cmap-class.md#removekey) et indirectement par [CMap::Lookup](cmap-class.md#lookup) et [CMap::Operator &#91;&#93;](cmap-class.md#operator_at).

La mise en œuvre par défaut crée une valeur de hachage en déplaçant le droit *de clé* par quatre positions. Remplacez cette fonction afin qu’elle renvoie des valeurs de hachage appropriées à votre application.

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

  **En-tête** afxtempl.h

## <a name="serializeelements"></a><a name="serializeelements"></a>SérialisationElements

[CArray](carray-class.md), [CList](clist-class.md), et [CMap](cmap-class.md) appellent cette fonction pour sérialiser les éléments.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments.

*Ar*<br/>
Un objet d’archives à archiver vers ou depuis.

*pElements*<br/>
Pointeur vers les éléments archivés.

*nCompte*<br/>
Nombre d’éléments archivés

### <a name="remarks"></a>Notes

L’implémentation par défaut fait un peu lire ou écrire.

Pour plus d’informations sur la mise en œuvre de cette fonction et d’autres fonctions d’aide, consultez l’article [Collections: How to Make a Type-Safe Collection](../how-to-make-a-type-safe-collection.md).

### <a name="example"></a>Exemple

Voir l’exemple dans l’article [Collections: How to Make a Type-Safe Collection](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxtempl.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CMap, classe](cmap-class.md)<br/>
[CList, classe](clist-class.md)<br/>
[Classe CArray](carray-class.md)
