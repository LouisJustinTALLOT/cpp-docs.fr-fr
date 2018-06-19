---
title: Vue d’ensemble du Marshaling dans C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1f950c8efbdd75e16096d158075e92594fb6b2d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137132"
---
# <a name="overview-of-marshaling-in-c"></a>Vue d’ensemble du marshaling dans C++
En mode mixte, vous devez parfois marshaler des données entre les types managés et natifs. [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] a introduit la bibliothèque de marshaling pour aider à marshaler et de convertir les données d’une manière simple.  
  
 Vous pouvez utiliser la bibliothèque de marshaling avec ou sans un [marshal_context, classe](../dotnet/marshal-context-class.md). Certaines conversions nécessitent un contexte. D’autres conversions peuvent être implémentées à l’aide de la [marshal_as](../dotnet/marshal-as.md) (fonction). Le tableau suivant répertorie les conversions actuels pris en charge, si elles nécessitent un contexte et quel fichier marshal, vous devez inclure :  
  
|À partir du type|Au type|Marshaler (méthode)|Fichier Include|  
|---------------|-------------|--------------------|------------------|  
|System::String ^|const char *|marshal_context|Marshal.h|  
|const char *|System::String ^|marshal_as|Marshal.h|  
|Char *|System::String ^|marshal_as|Marshal.h|  
|System::String ^|const wchar_t*|marshal_context|Marshal.h|  
|const wchar_t *|System::String ^|marshal_as|Marshal.h|  
|wchar_t *|System::String ^|marshal_as|Marshal.h|  
|System::IntPtr|HANDLE|marshal_as|marshal_windows.h|  
|HANDLE|System::IntPtr|marshal_as|marshal_windows.h|  
|System::String ^|BSTR|marshal_context|marshal_windows.h|  
|BSTR|System::String ^|marshal_as|Marshal.h|  
|System::String ^|bstr_t|marshal_as|marshal_windows.h|  
|bstr_t|System::String ^|marshal_as|marshal_windows.h|  
|System::String ^|std::String|marshal_as|marshal_cppstd.h|  
|std::String|System::String ^|marshal_as|marshal_cppstd.h|  
|System::String ^|std::wstring|marshal_as|marshal_cppstd.h|  
|std::wstring|System::String ^|marshal_as|marshal_cppstd.h|  
|System::String ^|CStringT\<char >|marshal_as|marshal_atl.h|  
|CStringT\<char >|System::String ^|marshal_as|marshal_atl.h|  
|System::String ^|CStringT < wchar_t >|marshal_as|marshal_atl.h|  
|CStringT < wchar_t >|System::String ^|marshal_as|marshal_atl.h|  
|System::String ^|CComBSTR|marshal_as|marshal_atl.h|  
|CComBSTR|System::String ^|marshal_as|marshal_atl.h|  
  
 Marshaling de nécessite un contexte uniquement lorsque marshaler des types de données managées en mode natif et que vous convertissez en type natif n’a pas d’un destructeur pour automatique de nettoyage. Le contexte de marshaling détruit le type de données natif allouées dans son destructeur. Par conséquent, les conversions qui requièrent un contexte sera valides jusqu'à ce que le contexte est supprimé. Pour enregistrer toutes les valeurs marshalés, vous devez copier les valeurs à vos propres variables.  
  
> [!NOTE]
>  Si vous avez incorporé `NULL`s dans votre chaîne, le résultat du marshaling de la chaîne n’est pas garanti. Le texte incorporé `NULL`s peut entraîner la chaîne à tronquer ou elles peuvent être conservées.  
  
 Les en-têtes de bibliothèque de marshaling sont situés dans le répertoire include dans le sous-répertoire msclr. Cet exemple montre comment inclure le répertoire msclr dans une déclaration d’en-tête include :  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 La bibliothèque de marshaling est extensible afin que vous pouvez ajouter vos propres types de marshaling. Pour plus d’informations sur l’extension de la bibliothèque de marshaling, consultez [Comment : étendre la bibliothèque de Marshaling](../dotnet/how-to-extend-the-marshaling-library.md).  
  
 Dans les versions antérieures, vous pouvez marshaler des données à l’aide de [appel de plateforme](/dotnet/framework/interop/consuming-unmanaged-dll-functions). Pour plus d’informations sur `PInvoke`, consultez [appelant les fonctions natives à partir de Code managé](../dotnet/calling-native-functions-from-managed-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque de prise en charge C++](../dotnet/cpp-support-library.md)   
 [Guide pratique pour étendre la bibliothèque de marshaling](../dotnet/how-to-extend-the-marshaling-library.md)