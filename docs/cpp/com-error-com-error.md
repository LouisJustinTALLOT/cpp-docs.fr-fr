---
description: 'En savoir plus sur : _com_error :: _com_error'
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 2c5b912f5d532e9aed5b8e84a3fe7e2fcd7d4100
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332567"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Spécifique à Microsoft**

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

*heure(s)*<br/>
Informations HRESULT.

*perrinfo*<br/>
Objet `IErrorInfo`.

*fAddRef*<br/>
Par défaut, le constructeur appelle AddRef sur une interface non null `IErrorInfo` . Cela fournit un décompte de références correct dans le cas courant où la propriété de l’interface est passée dans l’objet **_com_error** , par exemple :

```cpp
throw _com_error(hr, perrinfo);
```

Si vous ne souhaitez pas que votre code transfère la propriété à l’objet **_com_error** , et que l' `AddRef` est requis pour décaler le `Release` dans le destructeur **_com_error** , construisez l’objet comme suit :

```cpp
_com_error err(hr, perrinfo, true);
```

*que*<br/>
Objet **_com_error** existant.

## <a name="remarks"></a>Notes

Le premier constructeur crée un objet à partir d’un HRESULT et d’un `IErrorInfo` objet facultatif. Le deuxième crée une copie d’un objet **_com_error** existant.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
