---
description: 'En savoir plus sur : CFixedStringT, classe'
title: CFixedStringT, classe
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: a613716364318ced140709d2b33e9d9c4299af0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166834"
---
# <a name="cfixedstringt-class"></a>CFixedStringT, classe

Cette classe représente un objet String avec une mémoire tampon de caractères fixe.

## <a name="syntax"></a>Syntaxe

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Paramètres

*StringType*<br/>
Utilisé comme classe de base pour l’objet de chaîne fixe et peut être n’importe quel type de base `CStringT` . Voici quelques exemples : `CString` , `CStringA` et `CStringW` .

*t_nChars*<br/>
Nombre de caractères stockés dans la mémoire tampon.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFixedStringT :: CFixedStringT](#cfixedstringt)|Constructeur de l’objet String.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFixedStringT :: Operator =](#operator_eq)|Assigne une nouvelle valeur à un `CFixedStringT` objet.|

## <a name="remarks"></a>Notes

Cette classe est un exemple de classe de chaîne personnalisée basée sur `CStringT` . Bien que similaire, les deux classes diffèrent dans l’implémentation. Les principales différences entre `CFixedStringT` et `CStringT` sont les suivantes :

- La mémoire tampon de caractères initiale est allouée dans le cadre de l’objet et a une taille *t_nChars*. Cela permet `CFixedString` à l’objet d’occuper un segment de mémoire contigu à des fins de performances. Toutefois, si le contenu d’un `CFixedStringT` objet dépasse *t_nChars*, la mémoire tampon est allouée dynamiquement.

- La mémoire tampon de caractères d’un `CFixedStringT` objet est toujours de la même longueur ( *t_nChars*). Il n’existe aucune limitation quant à la taille de la mémoire tampon pour les `CStringT` objets.

- Le gestionnaire de mémoire pour `CFixedStringT` est personnalisé de sorte que le partage d’un objet [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) entre deux objets ou plus `CFixedStringT` n’est pas autorisé. `CStringT` les objets n’ont pas cette limitation.

Pour plus d’informations sur la personnalisation de `CFixedStringT` et la gestion de la mémoire pour les objets String en général, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Spécifications

**En-tête :** CStringT. h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a> CFixedStringT :: CFixedStringT

Construit un objet `CFixedStringT`.

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>Paramètres

*pszSrc*<br/>
Chaîne terminée par le caractère null à copier dans cet `CFixedStringT` objet.

*strSrc*<br/>
Objet existant `CFixedStringT` à copier dans cet `CFixedStringT` objet.

*pStringMgr*<br/>
Pointeur vers le gestionnaire de mémoire de l' `CFixedStringT` objet. Pour plus d’informations sur et sur la `IAtlStringMgr` gestion de la mémoire pour `CFixedStringT` , consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Notes

Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, vous devez savoir que des exceptions de mémoire peuvent se produire. Certains de ces constructeurs agissent comme des fonctions de conversion.

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a> CFixedStringT :: Operator =

Réinitialise un `CFixedStringT` objet existant avec de nouvelles données.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>Paramètres

*pszSrc*<br/>
Chaîne terminée par le caractère null à copier dans cet `CFixedStringT` objet.

*strSrc*<br/>
Existant `CFixedStringT` à copier dans cet `CFixedStringT` objet.

### <a name="remarks"></a>Notes

Vous devez savoir que des exceptions de mémoire peuvent se produire chaque fois que vous utilisez l’opérateur d’assignation, car un nouveau stockage est souvent alloué pour contenir l' `CFixedStringT` objet résultant.

## <a name="see-also"></a>Voir aussi

[CStringT (classe)](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
