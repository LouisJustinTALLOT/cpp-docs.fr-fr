---
title: marshal_context::marshal_as | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cc17010ccccc25679918bc02884774f1644dca69
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379129"
---
# <a name="marshalcontextmarshalas"></a>marshal_context::marshal_as

Effectue le marshaling sur un objet de données spécifique pour le convertir entre managé et un type de données natif.

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

Cette fonction effectue le marshaling sur un objet de données spécifique. Utilisez cette fonction uniquement avec les conversions indiquées par la table dans [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md).

Si vous tentez de marshaler une paire de types de données qui ne sont pas pris en charge, `marshal_as` générera une erreur [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) au moment de la compilation. Lire le message fourni avec cette erreur pour plus d’informations. Le `C4996` erreur peut être générée pour les fonctions plus de simplement déconseillées. Deux conditions qui génèrent cette erreur sont essaie de marshaler une paire de types de données qui ne sont pas prises en charge et essaie d’utiliser `marshal_as` pour une conversion qui requiert un contexte.

La bibliothèque de marshaling se compose de plusieurs fichiers d’en-tête. Toute conversion ne nécessite qu’un seul fichier, mais vous pouvez inclure des fichiers supplémentaires si vous avez besoin pour les autres conversions. Le tableau dans `Marshaling Overview in C++` indique quel fichier marshaling doit être inclus pour chaque conversion.

## <a name="example"></a>Exemple

Cet exemple crée un contexte pour le marshaling d’un `System::String` à un `const char *` type de variable. Les données converties ne seront plus valides après la ligne qui supprime le contexte.

```
// marshal_context_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   marshal_context^ context = gcnew marshal_context();
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = context->marshal_as<const char*>( message );
   delete context;
   return 0;
}
```

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête :** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, ou \<msclr\marshal_atl.h >

**Namespace :** msclr::interop

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context Class](../dotnet/marshal-context-class.md)