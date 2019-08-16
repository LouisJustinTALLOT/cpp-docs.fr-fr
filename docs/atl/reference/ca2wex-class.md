---
title: CA2WEX, classe
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
ms.openlocfilehash: 927b9f5031bb6262c2f4a071b535802eb9e6990a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497953"
---
# <a name="ca2wex-class"></a>CA2WEX, classe

Cette classe est utilisée par les macros de conversion de chaînes CA2TEX, CA2CTEX, CT2WEX et CT2CWEX, ainsi que les CA2W typedef.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CA2WEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
Taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est de 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|Constructeur.|
|[CA2WEX:: ~ CA2WEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CA2WEX:: Operator LPWSTR](#operator_lpwstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CA2WEX::m_psz](#m_psz)|Membre de données qui stocke la chaîne source.|
|[CA2WEX::m_szBuffer](#m_szbuffer)|Mémoire tampon statique, utilisée pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires ne soient requises, utilisez CA2TEX, CA2CTEX, CT2WEX, CT2CWEX ou CA2W dans votre code.

Cette classe contient une mémoire tampon statique de taille fixe qui est utilisée pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue de la mémoire à l’aide de **malloc**, en libérant la mémoire lorsque l’objet est hors de portée. Cela garantit que, contrairement aux macros de conversion de texte disponibles dans les versions précédentes d’ATL, cette classe peut être utilisée en toute sécurité dans les boucles et qu’elle ne déborde pas la pile.

Si la classe tente d’allouer de la mémoire sur le tas et échoue, `AtlThrow` elle appellera avec un argument de E_OUTOFMEMORY.

Par défaut, les macros et les classes de conversion ATL utilisent la page de codes ANSI du thread actuel pour la conversion. Si vous souhaitez substituer ce comportement pour une conversion spécifique, spécifiez la page de codes comme deuxième paramètre du constructeur pour la classe.

Les macros suivantes sont basées sur cette classe:

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

Le typedef suivant est basé sur cette classe:

- CA2W

Pour plus d’informations sur ces macros de conversion de texte, consultez macros de [conversion de chaînes ATL et MFC](string-conversion-macros.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes, consultez macros de [conversion de chaînes ATL et MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Configuration requise

**En-tête:** atlconv. h

##  <a name="ca2wex"></a>  CA2WEX::CA2WEX

Constructeur.

```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
Chaîne de texte à convertir.

*nCodePage*<br/>
Page de codes utilisée pour effectuer la conversion. Pour plus d’informations, consultez la discussion sur les paramètres de page de codes pour la fonction SDK Windows [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) .

### <a name="remarks"></a>Notes

Alloue la mémoire tampon utilisée dans le processus de traduction.

##  <a name="dtor"></a>CA2WEX:: ~ CA2WEX

Destructeur.

```
~CA2WEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

##  <a name="m_psz"></a>CA2WEX::m_psz

Membre de données qui stocke la chaîne source.

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CA2WEX::m_szBuffer

Mémoire tampon statique, utilisée pour stocker la chaîne convertie.

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>CA2WEX:: Operator LPWSTR

Opérateur de conversion.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte en tant que type LPWSTR.

## <a name="see-also"></a>Voir aussi

[CA2AEX, classe](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX, classe](../../atl/reference/ca2caex-class.md)<br/>
[CW2AEX, classe](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX, classe](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX, classe](../../atl/reference/cw2wex-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
