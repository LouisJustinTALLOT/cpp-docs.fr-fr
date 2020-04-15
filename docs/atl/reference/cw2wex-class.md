---
title: Classe CW2WEX
ms.date: 11/04/2016
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
ms.openlocfilehash: b116775a595f9fb3612d46e19526cf1396f85002
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330345"
---
# <a name="cw2wex-class"></a>Classe CW2WEX

Cette classe est utilisée par les macros de conversion des cordes CW2TEX et CT2WEX, et le Dactylo CW2W.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
La taille du tampon utilisé dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|Constructeur.|
|[CW2WEX: : CW2WEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX::opérateur LPWSTR](#operator_lpwstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|Le membre des données qui stocke la chaîne source.|
|[CW2WEX::m_szBuffer](#m_szbuffer)|Le tampon statique, utilisé pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CW2TEX, CT2WEX ou CW2W dans votre code.

Cette classe contient un tampon statique de taille fixe qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour s’adapter dans le tampon statique, la classe alloue la mémoire à l’aide **de malloc,** libérant la mémoire lorsque l’objet sort de portée. Cela garantit que, contrairement aux macros de conversion de texte disponibles dans les versions précédentes d’ATL, cette classe est sûre à utiliser en boucles et qu’elle ne débordera pas la pile.

Si la classe essaie d’allouer la mémoire `AtlThrow` sur le tas et échoue, il appellera avec un argument de E_OUTOFMEMORY.

Par défaut, les classes de conversion ET les macros ATL utilisent la page de code ANSI du thread actuel pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CW2TEX

- CT2WEX

Le tapdef suivant est basé sur cette classe :

- CW2W

Pour une discussion de ces macros de conversion de texte, voir [ATL et MFC String Conversion Macros](string-conversion-macros.md).

## <a name="example"></a>Exemple

Voir [les macros de conversion des cordes ATL et MFC](string-conversion-macros.md) par exemple en utilisant ces macros de conversion de cordes.

## <a name="requirements"></a>Spécifications

**En-tête:** atlconv.h

## <a name="cw2wexcw2wex"></a><a name="cw2wex"></a>CW2WEX::CW2WEX

Constructeur.

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
La chaîne de texte à convertir.

*nCodePage*<br/>
Page de codes. Pas utilisé dans cette classe.

### <a name="remarks"></a>Notes

Crée le tampon requis pour la traduction.

## <a name="cw2wexcw2wex"></a><a name="dtor"></a>CW2WEX: : CW2WEX

Le destructeur.

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Notes

Libère le tampon alloué.

## <a name="cw2wexm_psz"></a><a name="m_psz"></a>CW2WEX::m_psz

Le membre des données qui stocke la chaîne source.

```
LPWSTR m_psz;
```

## <a name="cw2wexm_szbuffer"></a><a name="m_szbuffer"></a>CW2WEX::m_szBuffer

Le tampon statique, utilisé pour stocker la chaîne convertie.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CW2WEX::opérateur LPWSTR

Opérateur de distribution.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPWSTR.

## <a name="see-also"></a>Voir aussi

[Classe CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Classe CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Classe CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Classe CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Classe CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
