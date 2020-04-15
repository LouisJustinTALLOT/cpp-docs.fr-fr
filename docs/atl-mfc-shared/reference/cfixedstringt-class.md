---
title: Classe CFixedStringT
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: fe096185f6f0b71ad45757cd0b75ab13c41e5f5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317824"
---
# <a name="cfixedstringt-class"></a>Classe CFixedStringT

Cette classe représente un objet à cordes avec un tampon de caractère fixe.

## <a name="syntax"></a>Syntaxe

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Paramètres

*StringType (en)*<br/>
Utilisé comme classe de base pour l’objet à chaîne fixe et peut être n’importe quel `CStringT`type basé. Voici quelques `CString` `CStringA`exemples, et `CStringW`.

*t_nChars*<br/>
Le nombre de caractères stockés dans le tampon.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFixedStringt::CFixedStringt](#cfixedstringt)|Le constructeur de l’objet à cordes.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFixedStringT::opérateur](#operator_eq)|Attribue une nouvelle valeur `CFixedStringT` à un objet.|

## <a name="remarks"></a>Notes

Cette classe est un exemple d’une classe de cordes personnalisée basée sur `CStringT`. Bien que similaires, les deux classes diffèrent dans la mise en œuvre. Les principales différences `CFixedStringT` `CStringT` entre et sont :

- Le tampon de caractère initial est attribué dans le cadre de l’objet et a la taille *t_nChars*. Cela permet `CFixedString` à l’objet d’occuper un morceau de mémoire contigus à des fins de performance. Toutefois, si le `CFixedStringT` contenu d’un objet dépasse *t_nChars,* le tampon est alloué dynamiquement.

- Le tampon de `CFixedStringT` caractère pour un objet est toujours de la même longueur ( *t_nChars*). Il n’y a `CStringT` aucune limitation de la taille du tampon pour les objets.

- Le gestionnaire `CFixedStringT` de mémoire pour est personnalisé de telle sorte que `CFixedStringT` le partage d’un objet [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) entre deux objets ou plus n’est pas autorisé. `CStringT`n’ont pas cette limitation.

Pour plus d’informations `CFixedStringT` sur la personnalisation et la gestion de la mémoire pour les objets à cordes en général, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Spécifications

**En-tête:** cstringt.h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a>CFixedStringt::CFixedStringt

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
Une corde à résilier `CFixedStringT` nulle à copier dans cet objet.

*strSrc (strSrc)*<br/>
Un `CFixedStringT` objet existant à copier `CFixedStringT` dans cet objet.

*pStringMgr*<br/>
Un pointeur pour le `CFixedStringT` gestionnaire de mémoire de l’objet. Pour plus `IAtlStringMgr` d’informations `CFixedStringT`sur et la gestion de la mémoire pour , voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Notes

Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, vous devez être conscient que des exceptions de mémoire peuvent en résulter. Certains de ces constructeurs agissent comme fonctions de conversion.

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a>CFixedStringT::opérateur

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
Une corde à résilier `CFixedStringT` nulle à copier dans cet objet.

*strSrc (strSrc)*<br/>
Un `CFixedStringT` existant à copier `CFixedStringT` dans cet objet.

### <a name="remarks"></a>Notes

Vous devez être conscient que des exceptions de mémoire peuvent se produire chaque `CFixedStringT` fois que vous utilisez l’opérateur d’affectation parce que le nouveau stockage est souvent alloué pour tenir l’objet résultant.

## <a name="see-also"></a>Voir aussi

[Classe CStringT](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
