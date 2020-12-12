---
description: 'En savoir plus sur : _com_raise_error'
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 81697b565104971d22da04a7b8b0e33a7f9255ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178210"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Spécifique à Microsoft**

Lève une [_com_error](../cpp/com-error-class.md) en réponse à un échec.

## <a name="syntax"></a>Syntaxe

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Paramètres

*heure(s)*<br/>
Informations HRESULT.

*perrinfo*<br/>
Objet `IErrorInfo`.

## <a name="remarks"></a>Notes

**_com_raise_error**, qui est défini dans \<comdef.h> , peut être remplacé par une version écrite par l’utilisateur du même nom et du même prototype. Cette opération peut être effectuée si vous souhaitez utiliser `#import` mais pas la gestion des exceptions C++. Dans ce cas, une version utilisateur de **_com_raise_error** peut décider d’effectuer une opération `longjmp` ou d’afficher une boîte de message et de l’arrêter. Toutefois, cette version utilisateur ne devrait pas être retournée, car le code de prise en charge COM du compilateur n'attend aucun retour de celle-ci.

Vous pouvez également utiliser [_set_com_error_handler](../cpp/set-com-error-handler.md) pour remplacer la fonction de gestion des erreurs par défaut.

Par défaut, **_com_raise_error** est défini comme suit :

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**FIN spécifique à Microsoft**

## <a name="requirements"></a>Spécifications

**En-tête :**\<comdef.h>

**Lib :** Si l' **wchar_t est** l’option du compilateur de type natif est on, utilisez comsuppw. lib ou comsuppwd. lib. Si **wchar_t est de type natif** , utilisez COMSUP. lib. Pour plus d’informations, consultez [/Zc:wchar_t (wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
