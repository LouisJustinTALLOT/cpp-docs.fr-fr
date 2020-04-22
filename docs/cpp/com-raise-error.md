---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: f5efbe98a489a380c4e9be5a0e40603be2a409c0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745083"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Microsoft Spécifique**

Jette un [_com_error](../cpp/com-error-class.md) en réponse à un échec.

## <a name="syntax"></a>Syntaxe

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Paramètres

*Hr*<br/>
INFORMATIONS HRESULT.

*perrinfo*<br/>
Objet `IErrorInfo`.

## <a name="remarks"></a>Notes

**_com_raise_error**, qui est définie \<dans comdef.h>, peut être remplacée par une version écrite par l’utilisateur du même nom et du même prototype. Cette opération peut être effectuée si vous souhaitez utiliser `#import` mais pas la gestion des exceptions C++. Dans ce cas, une **_com_raise_error** version utilisateur de _com_raise_error `longjmp` peut décider de faire un ou d’afficher une boîte de message et d’arrêter. Toutefois, cette version utilisateur ne devrait pas être retournée, car le code de prise en charge COM du compilateur n'attend aucun retour de celle-ci.

Vous pouvez également utiliser [_set_com_error_handler](../cpp/set-com-error-handler.md) pour remplacer la fonction de manipulation par défaut.

Par défaut, **_com_raise_error** est définie comme suit :

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**END Microsoft Spécifique**

## <a name="requirements"></a>Spécifications

**En-tête:** \<comdef.h>

**Lib:** Si le **wchar_t est l’option de** compilation de type autochtone est sur, utilisez comsuppw.lib ou comsuppwd.lib. Si **wchar_t est Native Type** est éteint, utilisez comsupp.lib. Pour plus d’informations, consultez [/Zc:wchar_t (wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
