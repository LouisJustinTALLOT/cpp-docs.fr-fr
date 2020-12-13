---
description: 'En savoir plus sur : classe CW2CWEX'
title: CW2CWEX, classe
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: 769dcedf1a9dc15129b09e3305330de33242562e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140229"
---
# <a name="cw2cwex-class"></a>CW2CWEX, classe

Cette classe est utilisée par les macros de conversion de chaînes CW2CTEX et CT2CWEX, ainsi que par le CW2W typedef.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
Taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|Constructeur.|
|[CW2CWEX :: ~ CW2CWEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CW2CWEX :: Operator LPCWSTR](#operator_lpcwstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CW2CWEX :: m_psz](#m_psz)|Membre de données qui stocke la chaîne source.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CW2CTEX, CT2CWEX ou CW2W dans votre code.

Cette classe peut être utilisée en toute sécurité dans les boucles et ne débordera pas la pile. Par défaut, les macros et les classes de conversion ATL utilisent la page de codes ANSI du thread actuel pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CW2CTEX

- CT2CWEX

Le typedef suivant est basé sur cette classe :

- CW2W

Pour plus d’informations sur ces macros de conversion de texte, consultez [macros de conversion de chaînes ATL et MFC](string-conversion-macros.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes [, consultez macros de conversion de chaînes ATL et MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Spécifications

**En-tête :** atlconv. h

## <a name="cw2cwexcw2cwex"></a><a name="cw2cwex"></a> CW2CWEX::CW2CWEX

Constructeur.

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Chaîne de texte à convertir.

*nCodePage*<br/>
Page de codes. Non utilisé dans cette classe.

### <a name="remarks"></a>Notes

Alloue la mémoire tampon utilisée dans le processus de traduction.

## <a name="cw2cwexcw2cwex"></a><a name="dtor"></a> CW2CWEX :: ~ CW2CWEX

Destructeur.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

## <a name="cw2cwexm_psz"></a><a name="m_psz"></a> CW2CWEX :: m_psz

Membre de données qui stocke la chaîne source.

```
LPCWSTR m_psz;
```

## <a name="cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a> CW2CWEX :: Operator LPCWSTR

Opérateur de conversion.

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la chaîne de texte en tant que type LPCWSTR.

## <a name="see-also"></a>Voir aussi

[CA2AEX, classe](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX, classe](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX, classe](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX, classe](../../atl/reference/cw2aex-class.md)<br/>
[CW2WEX, classe](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
