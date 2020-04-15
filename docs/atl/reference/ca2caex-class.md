---
title: Classe CA2CAEX
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: e6c727993b2907aaa551421a5d2d23e372b68917
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319145"
---
# <a name="ca2caex-class"></a>Classe CA2CAEX

Cette classe est utilisée par les macros de conversion des cordes CA2CTEX et CT2CAEX, et le tapdef CA2CA.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CA2CAEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
La taille du tampon utilisé dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Constructeur.|
|[CA2CAEX::CA2CAEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CA2CAEX::opérateur LPCSTR](#operator_lpcstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CA2CAEX::m_psz](#m_psz)|Le membre des données qui stocke la chaîne source.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CA2CTEX, CT2CAEX ou CA2CA dans votre propre code.

Cette classe est sûre à utiliser en boucles et ne débordera pas la pile. Par défaut, les classes et macros de conversion ATL utilisent la page de codes ANSI du thread actif pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CA2CTEX

- CT2CAEX

Le tapdef suivant est basé sur cette classe :

- CA2CA

Pour une discussion de ces macros de conversion de texte, voir [ATL et MFC String Conversion Macros](string-conversion-macros.md).

## <a name="example"></a>Exemple

Voir [les macros de conversion des cordes ATL et MFC](string-conversion-macros.md) par exemple en utilisant ces macros de conversion de cordes.

## <a name="requirements"></a>Spécifications

**En-tête:** atlconv.h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX

Constructeur.

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
La chaîne de texte à convertir.

*nCodePage*<br/>
Inutilisé dans cette classe.

### <a name="remarks"></a>Notes

Crée le tampon requis pour la traduction.

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX::CA2CAEX

Destructeur.

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>Notes

Libère le tampon alloué.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX::m_psz

Le membre des données qui stocke la chaîne source.

```
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX::opérateur LPCSTR

Opérateur de conversion.

```
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPCSTR.

## <a name="see-also"></a>Voir aussi

[Classe CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Classe CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Classe CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Classe CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Classe CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
