---
title: marshal_as
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2b2cacb0acf04aa40b3e299bffd7357e04916b16
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988130"
---
# <a name="marshal_as"></a>marshal_as

Cette méthode convertit les données entre les environnements natifs et managés.

## <a name="syntax"></a>Syntaxe

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Parameters

*input*<br/>
dans Valeur que vous souhaitez marshaler en une variable `To_Type`.

## <a name="return-value"></a>Valeur de retour

Variable de type `To_Type` qui correspond à la valeur convertie de `input`.

## <a name="remarks"></a>Notes

Cette méthode est un moyen simplifié de convertir les données entre les types natifs et managés. Pour déterminer les types de données pris en charge, consultez [vue d’ensemble C++du marshaling dans ](../dotnet/overview-of-marshaling-in-cpp.md). Certaines conversions de données requièrent un contexte. Vous pouvez convertir ces types de données à l’aide de la [classe marshal_context](../dotnet/marshal-context-class.md).

Si vous essayez de marshaler une paire de types de données qui ne sont pas pris en charge, `marshal_as` génère une erreur [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) au moment de la compilation. Pour plus d’informations, lisez le message fourni avec cette erreur. L’erreur `C4996` peut être générée pour des fonctions plus que simplement dépréciées. Par exemple, vous tentez de marshaler une paire de types de données qui ne sont pas pris en charge.

La bibliothèque de marshaling se compose de plusieurs fichiers d’en-tête. Toute conversion requiert un seul fichier, mais vous pouvez inclure des fichiers supplémentaires si nécessaire pour d’autres conversions. Pour savoir quelles conversions sont associées aux fichiers, recherchez dans le tableau `Marshaling Overview`. Quelle que soit la conversion que vous souhaitez effectuer, la spécification de l’espace de noms est toujours en vigueur.

Lève `System::ArgumentNullException(_EXCEPTION_NULLPTR)` si le paramètre d’entrée a la valeur null.

## <a name="example"></a>Exemple

Cet exemple marshale un `const char*` à un type de variable `System::String`.

```cpp
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>Configuration requise pour

**Fichier d’en-tête :** \<msclr\marshal.h >, \<msclr, \ marshal_windows. h >, \<msclr, \ marshal_cppstd. h > ou \<msclr, \ marshal_atl. h >

**Espace de noms :** msclr, :: Interop

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context Class](../dotnet/marshal-context-class.md)
