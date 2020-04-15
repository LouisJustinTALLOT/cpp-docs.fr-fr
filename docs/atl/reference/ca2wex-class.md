---
title: Classe CA2WEX
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: c9123e163ca828fa71fe217e46537ceb18e6f549
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319129"
---
# <a name="ca2wex-class"></a>Classe CA2WEX

Cette classe est utilisée par les macros de conversion de cordes CA2TEX, CA2CTEX, CT2WEX et CT2CWEX, et le tapdef CA2W.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CA2WEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
La taille du tampon utilisé dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|Constructeur.|
|[CA2WEX: :CA2WEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CA2WEX::opérateur LPWSTR](#operator_lpwstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CA2WEX::m_psz](#m_psz)|Le membre des données qui stocke la chaîne source.|
|[CA2WEX::m_szBuffer](#m_szbuffer)|Le tampon statique, utilisé pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CA2TEX, CA2CTEX, CT2WEX, CT2CWEX ou CA2W dans votre code.

Cette classe contient un tampon statique de taille fixe qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour s’adapter dans le tampon statique, la classe alloue la mémoire à l’aide **de malloc,** libérant la mémoire lorsque l’objet sort de portée. Cela garantit que, contrairement aux macros de conversion de texte disponibles dans les versions précédentes d’ATL, cette classe est sûre à utiliser en boucles et qu’elle ne débordera pas la pile.

Si la classe essaie d’allouer la mémoire `AtlThrow` sur le tas et échoue, il appellera avec un argument de E_OUTOFMEMORY.

Par défaut, les classes de conversion ET les macros ATL utilisent la page de code ANSI du thread actuel pour la conversion. Si vous souhaitez remplacer ce comportement pour une conversion spécifique, spécifiez la page de code comme deuxième paramètre pour le constructeur pour la classe.

Les macros suivantes sont basées sur cette classe :

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

Le tapdef suivant est basé sur cette classe :

- CA2W CA2W

Pour une discussion de ces macros de conversion de texte, voir [ATL et MFC String Conversion Macros](string-conversion-macros.md).

## <a name="example"></a>Exemple

Voir [les macros de conversion des cordes ATL et MFC](string-conversion-macros.md) par exemple en utilisant ces macros de conversion de cordes.

## <a name="requirements"></a>Spécifications

**En-tête:** atlconv.h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

Constructeur.

```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
La chaîne de texte à convertir.

*nCodePage*<br/>
La page de code utilisée pour effectuer la conversion. Voir la discussion de paramètres de page de code pour la fonction Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) pour plus de détails.

### <a name="remarks"></a>Notes

Alloue le tampon utilisé dans le processus de traduction.

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX: :CA2WEX

Destructeur.

```
~CA2WEX() throw();
```

### <a name="remarks"></a>Notes

Libère le tampon alloué.

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX::m_psz

Le membre des données qui stocke la chaîne source.

```
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX::m_szBuffer

Le tampon statique, utilisé pour stocker la chaîne convertie.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX::opérateur LPWSTR

Opérateur de conversion.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPWSTR.

## <a name="see-also"></a>Voir aussi

[Classe CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Classe CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Classe CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Classe CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Classe CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
