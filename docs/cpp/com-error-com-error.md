---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 4ac902f0fda90f77526ef53139ef0d523d8c22e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180782"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Section spécifique de Microsoft**

Construit un objet **_com_error** .

## <a name="syntax"></a>Syntaxe

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>Paramètres

*h*<br/>
Informations HRESULT.

*perrinfo*<br/>
Objet `IErrorInfo`.

*fAddRef*<br/>
Par défaut, le constructeur appelle AddRef sur une interface de `IErrorInfo` non null. Cela fournit un décompte de références correct dans le cas courant où la propriété de l’interface est passée dans l’objet **_com_error** , par exemple :

```cpp
throw _com_error(hr, perrinfo);
```

Si vous ne souhaitez pas que votre code transfère la propriété à l’objet **_com_error** , et que le `AddRef` est requis pour décaler le `Release` dans le destructeur **_com_error** , construisez l’objet comme suit :

```cpp
_com_error err(hr, perrinfo, true);
```

*comprenant*<br/>
Objet **_com_error** existant.

## <a name="remarks"></a>Notes

Le premier constructeur crée un objet à partir d’un HRESULT et d’un objet `IErrorInfo` facultatif. Le deuxième crée une copie d’un objet **_com_error** existant.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
