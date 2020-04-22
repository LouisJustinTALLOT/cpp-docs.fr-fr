---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: debad733f351c710ada342e29fa95a4d1ff03b7d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749809"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

Remplace la fonction par défaut utilisée pour la gestion des erreurs COM. **_set_com_error_handler** est spécifique à Microsoft.

## <a name="syntax"></a>Syntaxe

```cpp
void __stdcall _set_com_error_handler(
   void (__stdcall *pHandler)(
      HRESULT hr,
      IErrorInfo* perrinfo
   )
);
```

#### <a name="parameters"></a>Paramètres

*pHandler (en)*<br/>
Pointeur vers la fonction de remplacement.

*Hr*<br/>
INFORMATIONS HRESULT.

*perrinfo*<br/>
Objet `IErrorInfo`.

## <a name="remarks"></a>Notes

Par défaut, [_com_raise_error](../cpp/com-raise-error.md) gère toutes les erreurs de COM. Vous pouvez modifier ce comportement en utilisant **_set_com_error_handler** pour appeler votre propre fonction de manipulation des erreurs.

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

## <a name="requirements"></a>Spécifications

**En-tête:** \<comdef.h>

**Lib:** Si **l’option compilateur /Zc:wchar_t** est spécifiée (par défaut), utilisez comsuppw.lib ou comsuppwd.lib. Si **l’option /Zc:wchar_t-** compilateur est spécifiée, utilisez comsupp.lib. Pour plus d’informations, y compris comment définir cette option dans l’IDE, voir [/Zc:wchar_t (wchar_t Est de type autochtone)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)
