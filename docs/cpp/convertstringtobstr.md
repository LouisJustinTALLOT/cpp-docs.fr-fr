---
description: 'En savoir plus sur : ConvertStringToBSTR'
title: ConvertStringToBSTR
ms.date: 11/04/2016
f1_keywords:
- ConvertStringToBSTR
helpviewer_keywords:
- ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
ms.openlocfilehash: 7348fdec3448d17b51fd77385297422a8f10fd05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344599"
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR

**Spécifique à Microsoft**

Convertit une valeur `char *` en `BSTR`.

## <a name="syntax"></a>Syntaxe

```
BSTR __stdcall ConvertStringToBSTR(const char* pSrc)
```

#### <a name="parameters"></a>Paramètres

*pSrc*<br/>
`char *`Variable.

## <a name="example"></a>Exemple

```cpp
// ConvertStringToBSTR.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")
#pragma comment(lib, "kernel32.lib")

int main() {
   char* lpszText = "Test";
   printf_s("char * text: %s\n", lpszText);

   BSTR bstrText = _com_util::ConvertStringToBSTR(lpszText);
   wprintf_s(L"BSTR text: %s\n", bstrText);

   SysFreeString(bstrText);
}
```

```Output
char * text: Test
BSTR text: Test
```

**FIN spécifique à Microsoft**

## <a name="requirements"></a>Spécifications

**En-tête :**\<comutil.h>

**Lib :** comsuppw. lib ou comsuppwd. lib (consultez [/Zc : Wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)
