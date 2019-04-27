---
title: ConvertStringToBSTR
ms.date: 11/04/2016
f1_keywords:
- ConvertStringToBSTR
helpviewer_keywords:
- ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
ms.openlocfilehash: 5e7d8abd29033fc88dae1e83fcc6467fb0ace46f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154618"
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR

**Section spécifique à Microsoft**

Convertit un `char *` valeur à un `BSTR`.

## <a name="syntax"></a>Syntaxe

```
BSTR __stdcall ConvertStringToBSTR(const char* pSrc)
```

#### <a name="parameters"></a>Paramètres

*pSrc*<br/>
A `char *` variable.

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

**FIN de la section spécifique à Microsoft**

## <a name="requirements"></a>Configuration requise

**En-tête :** \<comutil.h >

**Lib :** comsuppw.lib ou comsuppwd.lib (voir [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)