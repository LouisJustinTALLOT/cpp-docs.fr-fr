---
title: marshal_context::marshal_as | Documents Microsoft
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
ms.openlocfilehash: 27f27b164d7a00e05e8d080a692f97b696776cbe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136205"
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
 [in] `input`  
 La valeur que vous souhaitez marshaler un `To_Type` variable.  
  
## <a name="return-value"></a>Valeur de retour  
 Une variable de type `To_Type` qui est la valeur convertie de `input`.  
  
## <a name="remarks"></a>Notes  
 Cette fonction effectue le marshaling d’un objet de données spécifique. Utilisez cette fonction uniquement avec les conversions indiquées par la table de [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
 Si vous tentez de marshaler une paire de types de données qui ne sont pas pris en charge, `marshal_as` génère une erreur [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) au moment de la compilation. Lisez le message fourni avec cette erreur pour plus d’informations. Le `C4996` erreur peut être générée pour les fonctions plus simplement déconseillées. Deux conditions qui génèrent cette erreur sont tente de marshaler une paire de types de données qui ne sont pas prises en charge et essayez d’utiliser `marshal_as` pour une conversion qui nécessite un contexte.  
  
 La bibliothèque de marshaling se compose de plusieurs fichiers d’en-tête. Toute conversion ne nécessite qu’un seul fichier, mais vous pouvez inclure des fichiers supplémentaires si vous avez besoin pour les autres conversions. La table `Marshaling Overview in C++` indique quel fichier marshaling doit être inclus pour chaque conversion.  
  
## <a name="example"></a>Exemple  
 Cet exemple crée un contexte pour le marshaling d’un `System::String` à un `const char *` le type de variable. Les données converties ne seront plus valides après la ligne qui supprime le contexte.  
  
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
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête :** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, ou \<msclr\marshal_atl.h >  
  
 **Namespace :** msclr::interop  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context Class](../dotnet/marshal-context-class.md)