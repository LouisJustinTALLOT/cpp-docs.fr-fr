---
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
ms.openlocfilehash: 41416c8223ac94364e8f83028ea93189e9f3f60c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373256"
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
Classe de base de la classe de carte de pointeur dactylographie; doit être une classe `CMapPtrToPtr` `CMapPtrToWord`de `CMapWordToPtr`carte `CMapStringToPtr`pointeur ( , , , , ou ).

*Clé*<br/>
Classe de l’objet utilisé comme la clé de la carte.

*Valeur*<br/>
Classe de l’objet stocké dans la carte.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Obtient le prochain élément pour itérer.|
|[CTypedPtrMap::Lookup](#lookup)|Retourne `KEY` un basé `VALUE`sur un .|
|[CTypedPtrMap::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|
|[CTypedPtrMap::SetAt](#setat)|Insère un élément dans la carte; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTypedPtrMap::opérateur \[\]](#operator_at)|Insère un élément dans la carte.|

## <a name="remarks"></a>Notes

Lorsque vous `CTypedPtrMap`utilisez, l’installation de vérification de type CMD permet d’éliminer les erreurs causées par des types de pointeurs dépareillés.

Étant `CTypedPtrMap` donné que toutes les fonctions sont inlines, l’utilisation de ce modèle n’affecte pas de manière significative la taille ou la vitesse de votre code.

Pour plus d’informations sur l’utilisation `CTypedPtrMap`, voir les articles [Collections](../../mfc/collections.md) et [Template-Based Classes](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc

Récupère l’élément `rNextPosition`de la `rNextPosition` carte à , puis mises à jour pour se référer à l’élément suivant dans la carte.

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Spécifie une référence à une `GetNextAssoc` `BASE_CLASS`valeur POSITION retournée par un précédent ou **::GetStartPosition** appel.

*Clé*<br/>
Paramètre de modèle spécifiant le type de clés de la carte.

*rKey (en)*<br/>
Spécifie la clé retournée de l’élément récupéré.

*Valeur*<br/>
Paramètre de modèle spécifiant le type de valeurs de la carte.

*rValue (en)*<br/>
Spécifie la valeur retournée de l’élément récupéré.

### <a name="remarks"></a>Notes

Cette fonction est plus utile pour itérer à travers tous les éléments de la carte. Notez que la séquence de position n’est pas nécessairement la même que la séquence de valeur clé.

Si l’élément récupéré est le dernier de la `rNextPosition` carte, alors la nouvelle valeur est réglée à NULL.

Cette fonction en `BASE_CLASS`ligne appelle **::GetNextAssoc**.

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a>CTypedPtrMap::Lookup

`Lookup`utilise un algorithme de hachage pour trouver rapidement l’élément de carte avec une clé qui correspond exactement.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Paramètre de modèle spécifiant la classe de base de la classe de cette carte.

*key*<br/>
La clé de l’élément à lever.

*Valeur*<br/>
Paramètre de modèle spécifiant le type de valeurs stockées dans cette carte.

*rValue (en)*<br/>
Spécifie la valeur retournée de l’élément récupéré.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément a été trouvé; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction en `BASE_CLASS`ligne appelle **::Lookup**.

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a>CTypedPtrMap::opérateur [ ]

Cet opérateur ne peut être utilisé que sur le côté gauche d’une déclaration d’affectation (une valeur l).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Paramètres

*Valeur*<br/>
Paramètre de modèle spécifiant le type de valeurs stockées dans cette carte.

*BASE_CLASS*<br/>
Paramètre de modèle spécifiant la classe de base de la classe de cette carte.

*key*<br/>
La clé de l’élément à lever ou à créer dans la carte.

### <a name="remarks"></a>Notes

S’il n’y a pas d’élément de carte avec la clé spécifiée, un nouvel élément est créé. Il n’y a pas d’équivalent « côté droit » (r-valeur) à cet opérateur parce qu’il est possible qu’une clé ne soit pas trouvée dans la carte. Utilisez `Lookup` la fonction membre pour la récupération d’éléments.

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a>CTypedPtrMap::RemoveKey

Cette fonction `BASE_CLASS`de membre appelle **::RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Paramètres

*Clé*<br/>
Paramètre de modèle spécifiant le type de clés de la carte.

*key*<br/>
Clé pour que l’élément soit enlevé.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’entrée a été trouvée et enlevée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

## <a name="ctypedptrmapsetat"></a><a name="setat"></a>CTypedPtrMap::SetAt

Cette fonction `BASE_CLASS`de membre appelle **::SetAt**.

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Paramètres

*Clé*<br/>
Paramètre de modèle spécifiant le type de clés de la carte.

*key*<br/>
Spécifie la valeur clé de la nouvelleValue.

*newValue*<br/>
Spécifie le pointeur d’objet qui est la valeur du nouvel élément.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr, classe](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord, classe](../../mfc/reference/cmapptrtoword-class.md)<br/>
[Classe CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[Classe CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)
