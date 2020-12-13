---
description: 'En savoir plus sur : classe CW2AEX'
title: CW2AEX, classe
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
ms.openlocfilehash: dfb654c43f2549cc1cfe58be064b2e6b9621fc69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140281"
---
# <a name="cw2aex-class"></a>CW2AEX, classe

Cette classe est utilisée par les macros de conversion de chaînes CT2AEX, CW2TEX, CW2CTEX et CT2CAEX, ainsi que les CW2A typedef.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
Taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Constructeur.|
|[CW2AEX :: ~ CW2AEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX :: Operator LPSTR](#operator_lpstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX :: m_psz](#m_psz)|Membre de données qui stocke la chaîne source.|
|[CW2AEX :: m_szBuffer](#m_szbuffer)|Mémoire tampon statique, utilisée pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CT2AEX, CW2TEX, CW2CTEX, CT2CAEX ou CW2A dans votre code.

Cette classe contient une mémoire tampon statique de taille fixe qui est utilisée pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue de la mémoire à l’aide de **malloc**, en libérant la mémoire lorsque l’objet est hors de portée. Cela garantit que, contrairement aux macros de conversion de texte disponibles dans les versions précédentes d’ATL, cette classe peut être utilisée en toute sécurité dans les boucles et qu’elle ne déborde pas la pile.

Si la classe tente d’allouer de la mémoire sur le tas et échoue, elle appellera `AtlThrow` avec un argument de E_OUTOFMEMORY.

Par défaut, les macros et les classes de conversion ATL utilisent la page de codes ANSI du thread actuel pour la conversion. Si vous souhaitez substituer ce comportement pour une conversion spécifique, spécifiez la page de codes comme deuxième paramètre du constructeur pour la classe.

Les macros suivantes sont basées sur cette classe :

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Le typedef suivant est basé sur cette classe :

- CW2A

Pour plus d’informations sur ces macros de conversion de texte, consultez [macros de conversion de chaînes ATL et MFC](string-conversion-macros.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes [, consultez macros de conversion de chaînes ATL et MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Spécifications

**En-tête :** atlconv. h

## <a name="cw2aexcw2aex"></a><a name="cw2aex"></a> CW2AEX::CW2AEX

Constructeur.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Chaîne de texte à convertir.

*nCodePage*<br/>
Page de codes utilisée pour effectuer la conversion. Pour plus d’informations, consultez la discussion sur les paramètres de page de codes pour la fonction SDK Windows [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) .

### <a name="remarks"></a>Notes

Alloue la mémoire tampon utilisée dans le processus de traduction.

## <a name="cw2aexcw2aex"></a><a name="dtor"></a> CW2AEX :: ~ CW2AEX

Destructeur.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

## <a name="cw2aexm_psz"></a><a name="m_psz"></a> CW2AEX :: m_psz

Membre de données qui stocke la chaîne source.

```
LPSTR m_psz;
```

## <a name="cw2aexm_szbuffer"></a><a name="m_szbuffer"></a> CW2AEX :: m_szBuffer

Mémoire tampon statique, utilisée pour stocker la chaîne convertie.

```
char m_szBuffer[t_nBufferLength];
```

## <a name="cw2aexoperator-lpstr"></a><a name="operator_lpstr"></a> CW2AEX :: Operator LPSTR

Opérateur de conversion.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la chaîne de texte en tant que type LPSTR.

## <a name="see-also"></a>Voir aussi

[CA2AEX, classe](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX, classe](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX, classe](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX, classe](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX, classe](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
