---
description: 'En savoir plus sur : ConvertBSTRToString'
title: ConvertBSTRToString
ms.date: 11/04/2016
f1_keywords:
- ConvertBSTRToString
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
ms.openlocfilehash: 72d6033003f186f358d9b4143498df65858ee354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344612"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Spécifique à Microsoft**

Convertit une valeur `BSTR` en `char *`.

## <a name="syntax"></a>Syntaxe

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>Paramètres

*pSrc*<br/>
Variable BSTR.

## <a name="remarks"></a>Notes

**ConvertBSTRToString** alloue une chaîne que vous devez supprimer.

## <a name="example"></a>Exemple

```cpp
// ConvertBSTRToString.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")

int main() {
   BSTR bstrText = ::SysAllocString(L"Test");
   wprintf_s(L"BSTR text: %s\n", bstrText);

   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);
   printf_s("char * text: %s\n", lpszText2);

   SysFreeString(bstrText);
   delete[] lpszText2;
}
```

```Output
BSTR text: Test
char * text: Test
```

**FIN spécifique à Microsoft**

## <a name="requirements"></a>Spécifications

**En-tête :**\<comutil.h>

**Lib :** comsuppw. lib ou comsuppwd. lib (consultez [/Zc : Wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)
