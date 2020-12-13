---
description: 'En savoir plus sur : classe CW2WEX'
title: CW2WEX, classe
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
ms.openlocfilehash: 87dbcefe37a54270b021ee1446ba5ccba2ef8313
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140242"
---
# <a name="cw2wex-class"></a>CW2WEX, classe

Cette classe est utilisée par les macros de conversion de chaînes CW2TEX et CT2WEX, ainsi que par le CW2W typedef.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
Taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|Constructeur.|
|[CW2WEX :: ~ CW2WEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX :: Operator LPWSTR](#operator_lpwstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX :: m_psz](#m_psz)|Membre de données qui stocke la chaîne source.|
|[CW2WEX :: m_szBuffer](#m_szbuffer)|Mémoire tampon statique, utilisée pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CW2TEX, CT2WEX ou CW2W dans votre code.

Cette classe contient une mémoire tampon statique de taille fixe qui est utilisée pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue de la mémoire à l’aide de **malloc**, en libérant la mémoire lorsque l’objet est hors de portée. Cela garantit que, contrairement aux macros de conversion de texte disponibles dans les versions précédentes d’ATL, cette classe peut être utilisée en toute sécurité dans les boucles et qu’elle ne déborde pas la pile.

Si la classe tente d’allouer de la mémoire sur le tas et échoue, elle appellera `AtlThrow` avec un argument de E_OUTOFMEMORY.

Par défaut, les macros et les classes de conversion ATL utilisent la page de codes ANSI du thread actuel pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CW2TEX

- CT2WEX

Le typedef suivant est basé sur cette classe :

- CW2W

Pour plus d’informations sur ces macros de conversion de texte, consultez [macros de conversion de chaînes ATL et MFC](string-conversion-macros.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes [, consultez macros de conversion de chaînes ATL et MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Spécifications

**En-tête :** atlconv. h

## <a name="cw2wexcw2wex"></a><a name="cw2wex"></a> CW2WEX::CW2WEX

Constructeur.

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Chaîne de texte à convertir.

*nCodePage*<br/>
Page de codes. Non utilisé dans cette classe.

### <a name="remarks"></a>Notes

Crée la mémoire tampon requise pour la traduction.

## <a name="cw2wexcw2wex"></a><a name="dtor"></a> CW2WEX :: ~ CW2WEX

Destructeur..

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

## <a name="cw2wexm_psz"></a><a name="m_psz"></a> CW2WEX :: m_psz

Membre de données qui stocke la chaîne source.

```
LPWSTR m_psz;
```

## <a name="cw2wexm_szbuffer"></a><a name="m_szbuffer"></a> CW2WEX :: m_szBuffer

Mémoire tampon statique, utilisée pour stocker la chaîne convertie.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a> CW2WEX :: Operator LPWSTR

Opérateur de conversion.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la chaîne de texte en tant que type LPWSTR.

## <a name="see-also"></a>Voir aussi

[CA2AEX, classe](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX, classe](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX, classe](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX, classe](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX, classe](../../atl/reference/cw2cwex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
