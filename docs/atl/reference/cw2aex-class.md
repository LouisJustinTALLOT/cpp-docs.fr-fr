---
title: Classe CW2AEX
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 849cbe5c26d7c7af7a8925a26057b5777554471d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330454"
---
# <a name="cw2aex-class"></a>Classe CW2AEX

Cette classe est utilisée par les macros de conversion des cordes CT2AEX, CW2TEX, CW2CTEX et CT2CAEX, ainsi que par le Dactylo CW2A.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
La taille du tampon utilisé dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Constructeur.|
|[CW2AEX::CW2AEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX::opérateur LPSTR](#operator_lpstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Le membre des données qui stocke la chaîne source.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Le tampon statique, utilisé pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CT2AEX, CW2TEX, CW2CTEX, CT2CAEX ou CW2A dans votre code.

Cette classe contient un tampon statique de taille fixe qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour s’adapter dans le tampon statique, la classe alloue la mémoire à l’aide **de malloc,** libérant la mémoire lorsque l’objet sort de portée. Cela garantit que, contrairement aux macros de conversion de texte disponibles dans les versions précédentes d’ATL, cette classe est sûre à utiliser en boucles et qu’elle ne débordera pas la pile.

Si la classe essaie d’allouer la mémoire `AtlThrow` sur le tas et échoue, il appellera avec un argument de E_OUTOFMEMORY.

Par défaut, les classes de conversion ET les macros ATL utilisent la page de code ANSI du thread actuel pour la conversion. Si vous souhaitez remplacer ce comportement pour une conversion spécifique, spécifiez la page de code comme deuxième paramètre pour le constructeur pour la classe.

Les macros suivantes sont basées sur cette classe :

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Le tapdef suivant est basé sur cette classe :

- CW2A

Pour une discussion de ces macros de conversion de texte, voir [ATL et MFC String Conversion Macros](string-conversion-macros.md).

## <a name="example"></a>Exemple

Voir [les macros de conversion des cordes ATL et MFC](string-conversion-macros.md) par exemple en utilisant ces macros de conversion de cordes.

## <a name="requirements"></a>Spécifications

**En-tête:** atlconv.h

## <a name="cw2aexcw2aex"></a><a name="cw2aex"></a>CW2AEX::CW2AEX

Constructeur.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*Zsp*<br/>
La chaîne de texte à convertir.

*nCodePage*<br/>
La page de code utilisée pour effectuer la conversion. Voir la discussion de paramètres de page de code pour la fonction Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) pour plus de détails.

### <a name="remarks"></a>Notes

Alloue le tampon utilisé dans le processus de traduction.

## <a name="cw2aexcw2aex"></a><a name="dtor"></a>CW2AEX::CW2AEX

Destructeur.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Notes

Libère le tampon alloué.

## <a name="cw2aexm_psz"></a><a name="m_psz"></a>CW2AEX::m_psz

Le membre des données qui stocke la chaîne source.

```
LPSTR m_psz;
```

## <a name="cw2aexm_szbuffer"></a><a name="m_szbuffer"></a>CW2AEX::m_szBuffer

Le tampon statique, utilisé pour stocker la chaîne convertie.

```
char m_szBuffer[t_nBufferLength];
```

## <a name="cw2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CW2AEX::opérateur LPSTR

Opérateur de conversion.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPSTR.

## <a name="see-also"></a>Voir aussi

[Classe CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Classe CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Classe CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Classe CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Classe CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
