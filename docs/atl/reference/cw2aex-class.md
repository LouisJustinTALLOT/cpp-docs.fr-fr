---
title: CW2AEX classe
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
ms.openlocfilehash: 97b398dd80bb38b1579458ae0b8b65f082458e23
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257915"
---
# <a name="cw2aex-class"></a>CW2AEX classe

Cette classe est utilisée par les macros de conversion de chaîne CT2AEX, CW2TEX, CW2CTEX, CT2CAEX et CW2A typedef.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
La taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Constructeur.|
|[CW2AEX::~CW2AEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX::operator LPSTR](#operator_lpstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Le membre de données qui stocke la chaîne source.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|La mémoire tampon statique, utilisé pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires sont requises, utilisez CT2AEX, CW2TEX, CW2CTEX, CT2CAEX ou CW2A dans votre code.

Cette classe contient une mémoire tampon de taille fixe statique qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue la mémoire à l’aide **malloc**, libère la mémoire quand l’objet est hors de portée. Cela garantit que, contrairement au texte des macros de conversion disponibles dans les versions précédentes d’ATL, cette classe est sûr à utiliser dans des boucles et qu’il ne dépassement de la pile.

Si la classe tente d’allouer de la mémoire sur le tas et échoue, il appellera `AtlThrow` avec l’argument E_OUTOFMEMORY.

Par défaut, les macros et les classes de conversion ATL utilisent page de codes ANSI du thread actuel pour la conversion. Si vous souhaitez substituer ce comportement pour une conversion spécifique, spécifiez la page de codes comme second paramètre au constructeur pour la classe.

Les macros suivantes sont basées sur cette classe :

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Le typedef suivant est basé sur cette classe :

- CW2A

Pour une description de ces macros de conversion de texte, consultez [Macros de Conversion de chaîne de MFC et ATL](string-conversion-macros.md).

## <a name="example"></a>Exemple

Consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md) pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes.

## <a name="requirements"></a>Spécifications

**En-tête :** atlconv.h

##  <a name="cw2aex"></a>  CW2AEX::CW2AEX

Constructeur.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
La chaîne de texte à convertir.

*nCodePage*<br/>
La page de codes utilisée pour effectuer la conversion. Consultez la discussion de paramètre de page de code pour la fonction Windows SDK [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar) pour plus d’informations.

### <a name="remarks"></a>Notes

Alloue la mémoire tampon utilisée dans le processus de traduction.

##  <a name="dtor"></a>  CW2AEX::~CW2AEX

Destructeur.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

##  <a name="m_psz"></a>  CW2AEX::m_psz

Le membre de données qui stocke la chaîne source.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer

La mémoire tampon statique, utilisé pour stocker la chaîne convertie.

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>  CW2AEX::operator LPSTR

Opérateur de conversion.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPSTR.

## <a name="see-also"></a>Voir aussi

[CA2AEX, classe](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX, classe](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX, classe](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX, classe](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX, classe](../../atl/reference/cw2wex-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
