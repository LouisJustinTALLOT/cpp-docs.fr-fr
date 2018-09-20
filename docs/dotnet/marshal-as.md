---
title: marshal_as | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a745c4d57ae721bb1891990c5621084a055dda3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389069"
---
# <a name="marshalas"></a>marshal_as

Cette méthode convertit des données entre les environnements natifs et managés.

## <a name="syntax"></a>Syntaxe

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Paramètres

*entrée*<br/>
[in] La valeur que vous souhaitez à marshaler en un `To_Type` variable.

## <a name="return-value"></a>Valeur de retour

Une variable de type `To_Type` qui représente la valeur convertie de `input`.

## <a name="remarks"></a>Notes

Cette méthode est un moyen simple pour convertir des données entre les types managés et natifs. Pour déterminer quels types de données sont pris en charge, consultez [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md). Certaines conversions de données nécessitent un contexte. Vous pouvez convertir ces types de données à l’aide de la [marshal_context Class](../dotnet/marshal-context-class.md).

Si vous tentez de marshaler une paire de types de données qui ne sont pas pris en charge, `marshal_as` générera une erreur [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) au moment de la compilation. Lire le message fourni avec cette erreur pour plus d’informations. Le `C4996` erreur peut être générée pour les fonctions plus de simplement déconseillées. Un exemple de ce tente de marshaler une paire de types de données qui ne sont pas pris en charge.

La bibliothèque de marshaling se compose de plusieurs fichiers d’en-tête. Toute conversion ne nécessite qu’un seul fichier, mais vous pouvez inclure des fichiers supplémentaires si vous avez besoin pour les autres conversions. Pour voir quelles conversions sont associées à quels fichiers, consultez dans la table `Marshaling Overview`. Peu importe quelle conversion vous voulez faire, l’exigence de l’espace de noms est toujours en vigueur.

## <a name="example"></a>Exemple

Cet exemple marshale à partir d’un `const char*` à un `System::String` type de variable.

```
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

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête :** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, ou \<msclr\marshal_atl.h >

**Namespace :** msclr::interop

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context Class](../dotnet/marshal-context-class.md)