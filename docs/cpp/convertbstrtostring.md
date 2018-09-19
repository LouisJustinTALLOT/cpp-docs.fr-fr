---
title: ConvertBSTRToString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- ConvertBSTRToString
dev_langs:
- C++
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c46ab493c6f3c80d9bee4b4b0c04d9569c12e23c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075878"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Section spécifique à Microsoft**

Convertit un `BSTR` valeur à un `char *`.

## <a name="syntax"></a>Syntaxe

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>Paramètres

*pSrc*<br/>
Variable BSTR.

## <a name="remarks"></a>Notes

**ConvertBSTRToString** alloue une chaîne, vous devez supprimer.

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

**FIN de la section spécifique à Microsoft**

## <a name="requirements"></a>Configuration requise

**En-tête :** \<comutil.h >

**Lib :** comsuppw.lib ou comsuppwd.lib (voir [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)