---
title: _com_error::_com_error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89377e33e56b0796fc850c050c8e79eac86ee07d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040464"
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

*ressources humaines*<br/>
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

*qui*<br/>
Un existant **_com_error** objet.

## <a name="remarks"></a>Notes

Le premier constructeur crée un nouvel objet étant donné un HRESULT et facultatifs `IErrorInfo` objet. Le deuxième constructeur crée une copie d’un existant **_com_error** objet.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)