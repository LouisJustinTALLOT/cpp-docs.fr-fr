---
title: Classe de CW2WEX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d888478be18063b00e1e5e8eabead510349584cf
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752533"
---
# <a name="cw2wex-class"></a>Classe de CW2WEX

Cette classe est utilisée par les macros de conversion de chaîne CW2TEX CT2WEX et CW2W typedef.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>  
class CW2WEX
```

#### <a name="parameters"></a>Paramètres

*t_nBufferLength*  
La taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est 128 octets.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|Constructeur.|
|[CW2WEX :: ~ CW2WEX](#dtor)|Destructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|Opérateur de conversion.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|Le membre de données qui stocke la chaîne source.|
|[CW2WEX::m_szBuffer](#m_szbuffer)|La mémoire tampon statique, utilisé pour stocker la chaîne convertie.|

## <a name="remarks"></a>Notes

À moins que des fonctionnalités supplémentaires sont requises, utilisez CW2TEX, CT2WEX ou CW2W dans votre code.

Cette classe contient une mémoire tampon de taille fixe statique qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue la mémoire à l’aide **malloc**, libère la mémoire quand l’objet est hors de portée. Cela garantit que, contrairement au texte des macros de conversion disponibles dans les versions précédentes d’ATL, cette classe est sûr à utiliser dans des boucles et qu’il ne dépassement de la pile.

Si la classe tente d’allouer de la mémoire sur le tas et échoue, il appellera `AtlThrow` avec l’argument E_OUTOFMEMORY.

Par défaut, les macros et les classes de conversion ATL utilisent page de codes ANSI du thread actuel pour la conversion.

Les macros suivantes sont basées sur cette classe :

- CW2TEX

- CT2WEX

Le typedef suivant est basé sur cette classe :

- CW2W

Pour une description de ces macros de conversion de texte, consultez [Macros de Conversion de chaîne de MFC et ATL](string-conversion-macros.md).

## <a name="example"></a>Exemple

Consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md) pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlconv.h

##  <a name="cw2wex"></a>  CW2WEX::CW2WEX

Constructeur.

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Paramètres

*psz*  
La chaîne de texte à convertir.

*nCodePage*  
La page de codes. Pas utilisé dans cette classe.

### <a name="remarks"></a>Notes

Crée la mémoire tampon requise pour la traduction.

##  <a name="dtor"></a>  CW2WEX :: ~ CW2WEX

Le destructeur...

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Notes

Libère la mémoire tampon allouée.

##  <a name="m_psz"></a>  CW2WEX::m_psz

Le membre de données qui stocke la chaîne source.

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2WEX::m_szBuffer

La mémoire tampon statique, utilisé pour stocker la chaîne convertie.

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>  CW2WEX::operator LPWSTR

Opérateur de cast.

```  
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la chaîne de texte comme type LPWSTR.

## <a name="see-also"></a>Voir aussi

[Classe de CA2AEX](../../atl/reference/ca2aex-class.md)   
[Classe de CA2CAEX](../../atl/reference/ca2caex-class.md)   
[Classe de CA2WEX](../../atl/reference/ca2wex-class.md)   
[CW2AEX classe](../../atl/reference/cw2aex-class.md)   
[Classe de CW2CWEX](../../atl/reference/cw2cwex-class.md)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
