---
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
ms.openlocfilehash: 6c7649b7131e3b1620112acf89867d0731d7265d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235159"
---
# <a name="cfixedstringt-class"></a>CFixedStringT, classe

Cette classe représente un objet string avec une mémoire tampon de caractères fixe.

## <a name="syntax"></a>Syntaxe

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Paramètres

*StringType*<br/>
Utilisé comme classe de base pour l’objet de chaîne fixe et peut être toute `CStringT`-type de base. Voici quelques exemples `CString`, `CStringA`, et `CStringW`.

*t_nChars*<br/>
Le nombre de caractères stockés dans la mémoire tampon.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|Le constructeur de l’objet string.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFixedStringT::operator =](#operator_eq)|Assigne une nouvelle valeur à un `CFixedStringT` objet.|

## <a name="remarks"></a>Notes

Cette classe est un exemple d’une classe de chaîne personnalisée basée sur `CStringT`. Bien que similaires, les deux classes diffèrent dans la mise en œuvre. Les principales différences entre `CFixedStringT` et `CStringT` sont :

- La mémoire tampon caractère initial est alloué dans le cadre de l’objet et a une taille *t_nChars*. Cela permet la `CFixedString` objet pour occuper un segment de mémoire contiguë à des fins de performances. Toutefois, si le contenu d’un `CFixedStringT` objet excède *t_nChars*, la mémoire tampon est allouée dynamiquement.

- La mémoire tampon de caractères pour un `CFixedStringT` objet est toujours la même longueur ( *t_nChars*). Il n’existe aucune limitation de taille de mémoire tampon pour `CStringT` objets.

- Le Gestionnaire de mémoire pour `CFixedStringT` personnalisé tel que le partage d’un [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) objet entre deux ou plusieurs `CFixedStringT` objets n’est pas autorisée. `CStringT` objets n’ont pas cette limitation.

Pour plus d’informations sur la personnalisation de `CFixedStringT` et gestion de la mémoire pour les objets string en général, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Configuration requise

**En-tête :** cstringt.h

##  <a name="cfixedstringt"></a>  CFixedStringT::CFixedStringT

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
Une chaîne se terminant par null doit être copié dans ce `CFixedStringT` objet.

*strSrc*<br/>
Un existant `CFixedStringT` objet doit être copié dans ce `CFixedStringT` objet.

*pStringMgr*<br/>
Un pointeur vers le Gestionnaire de mémoire de le `CFixedStringT` objet. Pour plus d’informations sur `IAtlStringMgr` et gestion de la mémoire pour `CFixedStringT`, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Notes

Étant donné que les constructeurs suivants copient les données d’entrée dans le nouveau stockage alloué, vous devez être conscient que la mémoire peuvent entraîner des exceptions. Certaines de ces constructeurs agissent en tant que fonctions de conversion.

##  <a name="operator_eq"></a>  CFixedStringT::operator =

Réinitialise un existant `CFixedStringT` objet avec de nouvelles données.

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
Une chaîne se terminant par null doit être copié dans ce `CFixedStringT` objet.

*strSrc*<br/>
Un existant `CFixedStringT` doit être copié dans ce `CFixedStringT` objet.

### <a name="remarks"></a>Notes

Vous devez être conscient que les exceptions peuvent se produire chaque fois que vous utilisez l’opérateur d’assignation, car il est souvent un nouveau stockage est alloué pour contenir le résultat de la mémoire `CFixedStringT` objet.

## <a name="see-also"></a>Voir aussi

[CStringT, classe](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
