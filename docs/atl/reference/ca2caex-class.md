---
title: CA2CAEX, classe
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: 505c1e369bc5949fea291a2172c16d5e52c75567
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168512"
---
# <a name="ca2caex-class"></a>CA2CAEX, classe

Cette classe est utilisée par les macros de conversion de chaînes CA2CTEX et CT2CAEX, ainsi que par le CA2CA typedef.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<int t_nBufferLength = 128>
class CA2CAEX
```

### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
Taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Constructeur.|
|[CA2CAEX :: ~ CA2CAEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CA2CAEX :: Operator LPCSTR](#operator_lpcstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CA2CAEX :: m_psz](#m_psz)|Membre de données qui stocke la chaîne source.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CA2CTEX, CT2CAEX ou CA2CA dans votre propre code.

Cette classe peut être utilisée en toute sécurité dans les boucles et ne débordera pas la pile. Par défaut, les classes et macros de conversion ATL utilisent la page de codes ANSI du thread actif pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CA2CTEX

- CT2CAEX

Le typedef suivant est basé sur cette classe :

- CA2CA

Pour plus d’informations sur ces macros de conversion de texte, consultez [macros de conversion de chaînes ATL et MFC](string-conversion-macros.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes [, consultez macros de conversion de chaînes ATL et MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Spécifications

**En-tête :** atlconv. h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX

Constructeur.

```cpp
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Chaîne de texte à convertir.

*nCodePage*<br/>
Inutilisé dans cette classe.

### <a name="remarks"></a>Notes

Crée la mémoire tampon requise pour la traduction.

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX :: ~ CA2CAEX

Destructeur.

```cpp
~CA2CAEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX :: m_psz

Membre de données qui stocke la chaîne source.

```cpp
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX :: Operator LPCSTR

Opérateur de conversion.

```cpp
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte en tant que type LPCSTR.

## <a name="see-also"></a>Voir aussi

[CA2AEX, classe](../../atl/reference/ca2aex-class.md)<br/>
[CA2WEX, classe](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX, classe](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX, classe](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX, classe](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
