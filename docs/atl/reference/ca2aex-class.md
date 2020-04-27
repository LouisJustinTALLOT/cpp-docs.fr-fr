---
title: CA2AEX, classe
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
ms.openlocfilehash: dfd8967d21005d83b38eeae36cfc147051d7beaf
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168525"
---
# <a name="ca2aex-class"></a>CA2AEX, classe

Cette classe est utilisée par les macros de conversion de chaînes CA2TEX et CT2AEX, ainsi que par le CA2A typedef.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <int t_nBufferLength = 128>
class CA2AEX
```

### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
Taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Constructeur.|
|[CA2AEX :: ~ CA2AEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX :: Operator LPSTR](#operator_lpstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX :: m_psz](#m_psz)|Membre de données qui stocke la chaîne source.|
|[CA2AEX :: m_szBuffer](#m_szbuffer)|Mémoire tampon statique, utilisée pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CA2TEX, CT2AEX ou CA2A dans votre propre code.

Cette classe contient une mémoire tampon statique de taille fixe qui est utilisée pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue de la mémoire à l’aide de **malloc**, en libérant la mémoire lorsque l’objet est hors de portée. Cela garantit que, contrairement aux macros de conversion de texte disponibles dans les versions précédentes d’ATL, cette classe peut être utilisée en toute sécurité dans les boucles et qu’elle ne déborde pas la pile.

Si la classe tente d’allouer de la mémoire sur le tas et échoue, `AtlThrow` elle appellera avec un argument de E_OUTOFMEMORY.

Par défaut, les macros et les classes de conversion ATL utilisent la page de codes ANSI du thread actuel pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CA2TEX

- CT2AEX

Le typedef suivant est basé sur cette classe :

- CA2A

Pour plus d’informations sur ces macros de conversion de texte, consultez [macros de conversion de chaînes ATL et MFC](string-conversion-macros.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes [, consultez macros de conversion de chaînes ATL et MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Spécifications

**En-tête :** atlconv. h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

Constructeur.

```cpp
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Chaîne de texte à convertir.

*nCodePage*<br/>
Inutilisé dans cette classe.

### <a name="remarks"></a>Notes

Crée la mémoire tampon requise pour la traduction.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX :: ~ CA2AEX

Destructeur.

```cpp
~CA2AEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX :: m_psz

Membre de données qui stocke la chaîne source.

```cpp
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX :: m_szBuffer

Mémoire tampon statique, utilisée pour stocker la chaîne convertie.

```cpp
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX :: Operator LPSTR

Opérateur de conversion.

```cpp
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte en tant que type LPSTR.

## <a name="see-also"></a>Voir aussi

[CA2CAEX, classe](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX, classe](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX, classe](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX, classe](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX, classe](../../atl/reference/cw2wex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
