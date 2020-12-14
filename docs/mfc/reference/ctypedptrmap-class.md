---
description: 'En savoir plus sur : classe CTypedPtrMap'
title: CTypedPtrMap, classe
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: 25476a9195fe4a522ed31937dc1e2c5156ef6792
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344989"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap, classe

Fournit un « wrapper » de type sécurisé pour les objets des classes de mappage de pointeur `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`et `CMapStringToPtr`.

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de mappage de pointeur typée ; doit être une classe de mappage de pointeur ( `CMapPtrToPtr` , `CMapPtrToWord` , `CMapWordToPtr` ou `CMapStringToPtr` ).

*KEY*<br/>
Classe de l’objet utilisé comme clé de la classe Map.

*VALUE*<br/>
Classe de l’objet stocké dans la classe Map.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTypedPtrMap :: GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour l’itération.|
|[CTypedPtrMap :: Lookup](#lookup)|Retourne un `KEY` basé sur un `VALUE` .|
|[CTypedPtrMap :: RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|
|[CTypedPtrMap :: SetAt](#setat)|Insère un élément dans la classe Map ; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTypedPtrMap ::, opérateur \[\]](#operator_at)|Insère un élément dans la classe Map.|

## <a name="remarks"></a>Notes

Lorsque vous utilisez `CTypedPtrMap` , la fonctionnalité de contrôle de type C++ permet d’éliminer les erreurs provoquées par des types pointeur incompatibles.

Étant donné que toutes les `CTypedPtrMap` fonctions sont Inline, l’utilisation de ce modèle n’affecte pas de manière significative la taille ou la vitesse de votre code.

Pour plus d’informations sur l’utilisation de `CTypedPtrMap` , consultez les articles [Collections](../../mfc/collections.md) et [classes basées sur des modèles](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a> CTypedPtrMap :: GetNextAssoc

Récupère l’élément cartographique à `rNextPosition` , puis met à jour `rNextPosition` pour faire référence à l’élément suivant dans la classe Map.

```cpp
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Spécifie une référence à une valeur de POSITION retournée par un `GetNextAssoc` appel précédent ou `BASE_CLASS` **:: GetStartPosition** .

*KEY*<br/>
Paramètre de modèle qui spécifie le type des clés de la carte.

*rKey*<br/>
Spécifie la clé retournée de l’élément récupéré.

*VALUE*<br/>
Paramètre de modèle qui spécifie le type des valeurs de la carte.

*rValue*<br/>
Spécifie la valeur retournée par l’élément récupéré.

### <a name="remarks"></a>Notes

Cette fonction est particulièrement utile pour itérer au sein de tous les éléments de la classe Map. Notez que la séquence de position n’est pas nécessairement la même que la séquence de valeur de clé.

Si l’élément récupéré est le dernier dans le mappage, la nouvelle valeur de `rNextPosition` est définie sur null.

Cette fonction inline appelle `BASE_CLASS` **:: GetNextAssoc**.

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a> CTypedPtrMap :: Lookup

`Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément cartographique avec une clé qui correspond exactement.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Paramètre de modèle spécifiant la classe de base de la classe de ce mappage.

*key*<br/>
Clé de l’élément à rechercher.

*VALUE*<br/>
Paramètre de modèle qui spécifie le type de valeurs stockées dans ce mappage.

*rValue*<br/>
Spécifie la valeur retournée par l’élément récupéré.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’élément a été trouvé ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction inline appelle `BASE_CLASS` **:: Lookup**.

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a> CTypedPtrMap :: Operator []

Cet opérateur peut être utilisé uniquement sur le côté gauche d’une instruction d’assignation (une l-value).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Paramètres

*VALUE*<br/>
Paramètre de modèle qui spécifie le type de valeurs stockées dans ce mappage.

*BASE_CLASS*<br/>
Paramètre de modèle spécifiant la classe de base de la classe de ce mappage.

*key*<br/>
Clé de l’élément à rechercher ou à créer dans le mappage.

### <a name="remarks"></a>Notes

S’il n’y a pas d’élément cartographique avec la clé spécifiée, un nouvel élément est créé. Il n’y a aucun « côté droit » (r-value) équivalent à cet opérateur, car il est possible qu’une clé ne soit pas trouvée dans le mappage. Utilisez la `Lookup` fonction membre pour la récupération d’élément.

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a> CTypedPtrMap :: RemoveKey

Cette fonction membre appelle `BASE_CLASS` **:: RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Paramètres

*KEY*<br/>
Paramètre de modèle qui spécifie le type des clés de la carte.

*key*<br/>
Clé pour l’élément à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’entrée a été trouvée et supprimée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour obtenir des remarques plus détaillées, consultez [CMapStringToOb :: RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

## <a name="ctypedptrmapsetat"></a><a name="setat"></a> CTypedPtrMap :: SetAt

Cette fonction membre appelle `BASE_CLASS` **:: setat**.

```cpp
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Paramètres

*KEY*<br/>
Paramètre de modèle qui spécifie le type des clés de la carte.

*key*<br/>
Spécifie la valeur de clé de newValue.

*newValue*<br/>
Spécifie le pointeur d’objet qui est la valeur du nouvel élément.

### <a name="remarks"></a>Notes

Pour obtenir des remarques plus détaillées, consultez [CMapStringToOb :: setat](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr, classe](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord, classe](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr, classe](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr, classe](../../mfc/reference/cmapstringtoptr-class.md)
