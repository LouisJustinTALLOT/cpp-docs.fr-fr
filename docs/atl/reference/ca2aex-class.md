---
title: Classe CA2AEX
ms.date: 11/04/2016
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
ms.openlocfilehash: 4f8b9f91e9bc499523fe3484bc76325e2efb8140
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319179"
---
# <a name="ca2aex-class"></a>Classe CA2AEX

Cette classe est utilisée par les macros de conversion des cordes CA2TEX et CT2AEX, et le typedef CA2A.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
La taille du tampon utilisé dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Constructeur.|
|[CA2AEX::CA2AEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX::opérateur LPSTR](#operator_lpstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX:m_psz](#m_psz)|Le membre des données qui stocke la chaîne source.|
|[CA2AEX::m_szBuffer](#m_szbuffer)|Le tampon statique, utilisé pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CA2TEX, CT2AEX ou CA2A dans votre propre code.

Cette classe contient un tampon statique de taille fixe qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour s’adapter dans le tampon statique, la classe alloue la mémoire à l’aide **de malloc,** libérant la mémoire lorsque l’objet sort de portée. Cela garantit que, contrairement aux macros de conversion de texte disponibles dans les versions précédentes d’ATL, cette classe est sûre à utiliser en boucles et qu’elle ne débordera pas la pile.

Si la classe essaie d’allouer la mémoire `AtlThrow` sur le tas et échoue, il appellera avec un argument de E_OUTOFMEMORY.

Par défaut, les classes de conversion ET les macros ATL utilisent la page de code ANSI du thread actuel pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CA2TEX

- CT2AEX

Le tapdef suivant est basé sur cette classe :

- CA2A

Pour une discussion de ces macros de conversion de texte, voir [ATL et MFC String Conversion Macros](string-conversion-macros.md).

## <a name="example"></a>Exemple

Voir [les macros de conversion des cordes ATL et MFC](string-conversion-macros.md) par exemple en utilisant ces macros de conversion de cordes.

## <a name="requirements"></a>Spécifications

**En-tête:** atlconv.h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

Constructeur.

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
La chaîne de texte à convertir.

*nCodePage*<br/>
Inutilisé dans cette classe.

### <a name="remarks"></a>Notes

Crée le tampon requis pour la traduction.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX::CA2AEX

Destructeur.

```
~CA2AEX() throw();
```

### <a name="remarks"></a>Notes

Libère le tampon alloué.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX:m_psz

Le membre des données qui stocke la chaîne source.

```
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX::m_szBuffer

Le tampon statique, utilisé pour stocker la chaîne convertie.

```
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX::opérateur LPSTR

Opérateur de conversion.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPSTR.

## <a name="see-also"></a>Voir aussi

[Classe CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Classe CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Classe CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Classe CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Classe CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
