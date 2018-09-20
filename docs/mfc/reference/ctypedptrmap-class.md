---
title: CTypedPtrMap, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85f44473237a17a83aae2377e63a4e35d43483b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433788"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap (classe)

Fournit un « wrapper » de type sécurisé pour les objets des classes de mappage de pointeur `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`et `CMapStringToPtr`.

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe map de pointeurs typés ; doit être une classe de carte de pointeur ( `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, ou `CMapStringToPtr`).

*KEY*<br/>
Classe de l’objet utilisé comme clé pour la carte.

*VALEUR*<br/>
Classe de l’objet stocké dans la classe map.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour une itération.|
|[CTypedPtrMap::Lookup](#lookup)|Retourne un `KEY` selon un `VALUE`.|
|[CTypedPtrMap::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|
|[CTypedPtrMap::SetAt](#setat)|Insère un élément dans l’objet map. remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[[] CTypedPtrMap::operator](#operator_at)|Insère un élément dans la classe map.|

## <a name="remarks"></a>Notes

Lorsque vous utilisez `CTypedPtrMap`, la fonctionnalité de vérification de type C++ permet d’éliminer les erreurs provoquées par les types de pointeur qui ne correspondent pas.

Étant donné que tous les `CTypedPtrMap` fonctions inline, utilisation de ce modèle ne pas affecte de manière significative la taille ou la vitesse de votre code.

Pour plus d’informations sur l’utilisation de `CTypedPtrMap`, consultez les articles [Collections](../../mfc/collections.md) et [Classes basées sur le modèle](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtempl.h

##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc

Récupère l’élément de carte à `rNextPosition`, puis met à jour `rNextPosition` pour faire référence à l’élément suivant dans la carte.

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Spécifie une référence à une valeur POSITION retournée par une précédente `GetNextAssoc` ou `BASE_CLASS` **:: GetStartPosition** appeler.

*KEY*<br/>
Paramètre de modèle qui spécifie le type des clés de la carte.

*rKey*<br/>
Spécifie la clé retournée de l’élément récupéré.

*VALEUR*<br/>
Paramètre de modèle qui spécifie le type des valeurs de la carte.

*rValue*<br/>
Spécifie la valeur retournée de l’élément récupéré.

### <a name="remarks"></a>Notes

Cette fonction est particulièrement utile pour itérer tous les éléments dans le mappage. Notez que la séquence de position n’est pas nécessairement identique à la séquence de la valeur de clé.

Si l’élément récupéré est le dernier dans le mappage, puis la nouvelle valeur de `rNextPosition` est définie sur NULL.

Cette fonction inline s’appelle `BASE_CLASS` **:: GetNextAssoc**.

##  <a name="lookup"></a>  CTypedPtrMap::Lookup

`Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément de carte avec une clé qui correspond exactement.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Paramètre de modèle en spécifiant la classe de base de la classe de cette carte.

*key*<br/>
La clé de l’élément à rechercher.

*VALEUR*<br/>
Paramètre de modèle qui spécifie le type des valeurs stockées dans ce mappage.

*rValue*<br/>
Spécifie la valeur retournée de l’élément récupéré.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément a été trouvé ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction inline s’appelle `BASE_CLASS` **:: recherche**.

##  <a name="operator_at"></a>  [] CTypedPtrMap::operator

Cet opérateur peut être utilisé uniquement sur le côté gauche d’une instruction d’assignation (une l-value).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Paramètres

*VALEUR*<br/>
Paramètre de modèle qui spécifie le type des valeurs stockées dans ce mappage.

*BASE_CLASS*<br/>
Paramètre de modèle en spécifiant la classe de base de la classe de cette carte.

*key*<br/>
La clé de l’élément recherché ou la création de la carte.

### <a name="remarks"></a>Notes

S’il n’existe aucun élément de mappage avec la clé spécifiée, un nouvel élément est créé. Aucun (r-value) « droite » n’est équivalent à cet opérateur, car il est possible qu’une clé peut être introuvable dans le mappage. Utilisez le `Lookup` fonction membre pour l’extraction d’un élément.

##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey

Cette fonction membre appelle `BASE_CLASS` **:: RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Paramètres

*KEY*<br/>
Paramètre de modèle qui spécifie le type des clés de la carte.

*key*<br/>
Clé de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’entrée a été trouvée et supprimée avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

##  <a name="setat"></a>  CTypedPtrMap::SetAt

Cette fonction membre appelle `BASE_CLASS` **:: SetAt**.

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Paramètres

*KEY*<br/>
Paramètre de modèle qui spécifie le type des clés de la carte.

*key*<br/>
Spécifie la valeur de clé de la newValue.

*newValue*<br/>
Spécifie le pointeur d’objet qui est la valeur du nouvel élément.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Voir aussi

[Exemple MFC COLLECT](../../visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr, classe](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord, classe](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr, classe](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr, classe](../../mfc/reference/cmapstringtoptr-class.md)
