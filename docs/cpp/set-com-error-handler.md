---
title: _set_com_error_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 192707fe15560adb816b530ecf0e67713ae7d302
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092555"
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler

**Section spécifique à Microsoft**

Remplace la fonction par défaut utilisée pour la gestion des erreurs COM.

## <a name="syntax"></a>Syntaxe

```
void __stdcall _set_com_error_handler(
   void (__stdcall *pHandler)(
      HRESULT hr,
      IErrorInfo* perrinfo
   )
);
```

#### <a name="parameters"></a>Paramètres

*pHandler*<br/>
Pointeur vers la fonction de remplacement.

*ressources humaines*<br/>
Informations HRESULT.

*perrinfo*<br/>
Objet `IErrorInfo`.

## <a name="remarks"></a>Notes

Par défaut, [_com_raise_error](../cpp/com-raise-error.md) gère toutes les erreurs COM. Vous pouvez modifier ce comportement à l’aide de **_set_com_error_handler** pour appeler votre propre fonction de gestion des erreurs.

La fonction de remplacement doit avoir une signature qui est équivalente à celle de `_com_raise_error`.

## <a name="example"></a>Exemple

```cpp
// _set_com_error_handler.cpp
// compile with /EHsc
#include <stdio.h>
#include <comdef.h>
#include <comutil.h>

// Importing ado dll to attempt to establish an ado connection.
// Not related to _set_com_error_handler
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")

void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)
{
   throw "Unable to establish the connection!";
}

int main()
{
   _set_com_error_handler(_My_com_raise_error);
   _bstr_t bstrEmpty(L"");
   _ConnectionPtr Connection = NULL;
   try
   {
      Connection.CreateInstance(__uuidof(Connection));
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);
   }
   catch(char* errorMessage)
   {
      printf("Exception raised: %s\n", errorMessage);
   }

   return 0;
}
```

```Output
Exception raised: Unable to establish the connection!
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<comdef.h >

**Lib :** si le **wchar_t est un Type natif** option du compilateur est activé, utilisez comsuppw.lib ou comsuppwd.lib. Si **wchar_t est un Type natif** est désactivée, utilisez comsupp.lib. Pour plus d’informations, consultez [/Zc:wchar_t (wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)