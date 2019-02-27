---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 864236e86b4aeb6ce7b3315df57af1b577693c26
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954937"
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

*hr*<br/>
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

## <a name="requirements"></a>Spécifications

**En-tête :** \<comdef.h >

**Lib :** Si le **/Zc : wchar_t** option du compilateur est spécifiée (la valeur par défaut), utilisez comsuppw.lib ou comsuppwd.lib. Si le **/Zc :wchar_t-)** option du compilateur est spécifiée, utilisez comsupp.lib. Pour plus d’informations, y compris comment définir cette option dans l’IDE, consultez [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Voir aussi

[Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)
