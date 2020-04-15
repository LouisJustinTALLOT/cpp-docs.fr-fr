---
title: Classe CW2CWEX
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: 07dd0319586054403d8ed0c8efc813b4061e355a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330433"
---
# <a name="cw2cwex-class"></a>Classe CW2CWEX

Cette classe est utilisée par les macros de conversion des cordes CW2CTEX et CT2CWEX, et le Dactylo CW2W.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
La taille du tampon utilisé dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|Constructeur.|
|[CW2CWEX: :CW2CWEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CW2CWEX::opérateur LPCWSTR](#operator_lpcwstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|Le membre des données qui stocke la chaîne source.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CW2CTEX, CT2CWEX ou CW2W dans votre code.

Cette classe est sûre à utiliser en boucles et ne débordera pas la pile. Par défaut, les classes de conversion ET les macros ATL utilisent la page de code ANSI du thread actuel pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CW2CTEX

- CT2CWEX

Le tapdef suivant est basé sur cette classe :

- CW2W

Pour une discussion de ces macros de conversion de texte, voir [ATL et MFC String Conversion Macros](string-conversion-macros.md).

## <a name="example"></a>Exemple

Voir [les macros de conversion des cordes ATL et MFC](string-conversion-macros.md) par exemple en utilisant ces macros de conversion de cordes.

## <a name="requirements"></a>Spécifications

**En-tête:** atlconv.h

## <a name="cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX::CW2CWEX

Constructeur.

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
La chaîne de texte à convertir.

*nCodePage*<br/>
Page de codes. Pas utilisé dans cette classe.

### <a name="remarks"></a>Notes

Alloue le tampon utilisé dans le processus de traduction.

## <a name="cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX: :CW2CWEX

Destructeur.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Notes

Libère le tampon alloué.

## <a name="cw2cwexm_psz"></a><a name="m_psz"></a>CW2CWEX::m_psz

Le membre des données qui stocke la chaîne source.

```
LPCWSTR m_psz;
```

## <a name="cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX::opérateur LPCWSTR

Opérateur de conversion.

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPCWSTR.

## <a name="see-also"></a>Voir aussi

[Classe CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Classe CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Classe CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Classe CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Classe CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
