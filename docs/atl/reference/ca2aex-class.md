---
title: Classe de CA2AEX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49e364e2676242ad75f185792faa545bbb90ef1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071209"
---
# <a name="ca2aex-class"></a>Classe de CA2AEX

Cette classe est utilisée par les macros de conversion de chaîne CA2TEX CT2AEX et CA2A typedef.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*<br/>
La taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Constructeur.|
|[CA2AEX :: ~ CA2AEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX::operator LPSTR](#operator_lpstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CA2AEX::m_psz](#m_psz)|Le membre de données qui stocke la chaîne source.|
|[CA2AEX::m_szBuffer](#m_szbuffer)|La mémoire tampon statique, utilisé pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires sont requises, utilisez CA2TEX, CT2AEX ou CA2A dans votre propre code.

Cette classe contient une mémoire tampon de taille fixe statique qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue la mémoire à l’aide **malloc**, libère la mémoire quand l’objet est hors de portée. Cela garantit que, contrairement au texte des macros de conversion disponibles dans les versions précédentes d’ATL, cette classe est sûr à utiliser dans des boucles et qu’il ne dépassement de la pile.

Si la classe tente d’allouer de la mémoire sur le tas et échoue, il appellera `AtlThrow` avec l’argument E_OUTOFMEMORY.

Par défaut, les macros et les classes de conversion ATL utilisent page de codes ANSI du thread actuel pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CA2TEX

- CT2AEX

Le typedef suivant est basé sur cette classe :

- CA2A

Pour une description de ces macros de conversion de texte, consultez [Macros de Conversion de chaîne de MFC et ATL](string-conversion-macros.md).

## <a name="example"></a>Exemple

Consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md) pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlconv.h

##  <a name="ca2aex"></a>  CA2AEX::CA2AEX

Constructeur.

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*<br/>
La chaîne de texte à convertir.

*nCodePage*<br/>
Inutilisé dans cette classe.

### <a name="remarks"></a>Notes

Crée la mémoire tampon requise pour la traduction.

##  <a name="dtor"></a>  CA2AEX :: ~ CA2AEX

Destructeur.

```
~CA2AEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

##  <a name="m_psz"></a>  CA2AEX::m_psz

Le membre de données qui stocke la chaîne source.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CA2AEX::m_szBuffer

La mémoire tampon statique, utilisé pour stocker la chaîne convertie.

```
char m_szBuffer[ t_nBufferLength];
```

##  <a name="operator_lpstr"></a>  CA2AEX::operator LPSTR

Opérateur de conversion.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPSTR.

## <a name="see-also"></a>Voir aussi

[CA2CAEX, classe](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX, classe](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX, classe](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX, classe](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX, classe](../../atl/reference/cw2wex-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)