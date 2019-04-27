---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 8856289605cce430fdab36d6e3e8b743190e02ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155122"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error

**Section spécifique à Microsoft**

Construit un **_com_error** objet.

## <a name="syntax"></a>Syntaxe

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>Paramètres

*hr*<br/>
Informations HRESULT.

*perrinfo*<br/>
Objet `IErrorInfo`.

*fAddRef*<br/>
La valeur par défaut, le constructeur à appeler AddRef sur une valeur non null `IErrorInfo` interface. Ainsi, pour le décompte correct dans le cas courant où la propriété de l’interface est passée dans le **_com_error** l’objet, tel que :

```cpp
throw _com_error(hr, perrinfo);
```

Si vous ne souhaitez pas que votre code pour transférer la propriété à la **_com_error** objet et le `AddRef` est requis pour décaler la `Release` dans le **_com_error** destructeur, construire l’objet en tant que suit :

```cpp
_com_error err(hr, perrinfo, true);
```

*that*<br/>
Un existant **_com_error** objet.

## <a name="remarks"></a>Notes

Le premier constructeur crée un nouvel objet étant donné un HRESULT et facultatifs `IErrorInfo` objet. Le deuxième constructeur crée une copie d’un existant **_com_error** objet.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)