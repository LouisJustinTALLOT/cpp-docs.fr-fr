---
title: Vue d’ensemble du Marshaling dans C++ | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 747d9a67f7796b5a62115acf55343370aea77bdf
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207863"
---
# <a name="overview-of-marshaling-in-c"></a>Vue d’ensemble du marshaling dans C++
En mode mixte, vous devez parfois marshaler des données entre les types managés et natifs. Visual Studio 2008 a introduit le *bibliothèque de marshaling* pour aider à marshaler et de convertir les données d’une manière simple.  La bibliothèque de marshaling se compose d’un ensemble de fonctions et une `marshal_context` classe qui effectuent le marshaling pour les types courants. La bibliothèque est définie dans ces en-têtes dans le **inclure/msclr** répertoire correspondant à votre édition de Visual Studio :

|Header|Description|  
|---------------|-----------------|
|Marshal.h|`marshal_context` classe et des fonctions de marshaling sans contexte|
|marshal_atl.h| Fonctions pour le marshaling des types d’ATL|
|marshal_cppstd.h|Fonctions pour le marshaling des types C++ standard|
|marshal_windows.h|Fonctions pour le marshaling des types de Windows|


Le chemin d’accès par défaut pour **msclr** dossier est quelque chose comme ceci en fonction de l’édition que vous avez et le numéro de build :

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

 Vous pouvez utiliser la bibliothèque de marshaling avec ou sans un [marshal_context Class](../dotnet/marshal-context-class.md). Certaines conversions nécessitent un contexte. D’autres conversions peuvent être implémentées à l’aide de la [marshal_as](../dotnet/marshal-as.md) (fonction). Le tableau suivant répertorie les conversions actuels pris en charge, si elles nécessitent un contexte et quel fichier marshal, vous devez inclure :  
  
|À partir de type|En type|Marshaler (méthode)|Fichier Include|  
|---------------|-------------|--------------------|------------------|  
|System::String ^|const char \*|marshal_context|Marshal.h|  
|const char \*|System::String ^|marshal_as|Marshal.h|  
|Char \*|System::String ^|marshal_as|Marshal.h|  
|System::String ^|wchar_t const\*|marshal_context|Marshal.h|  
|wchar_t const \*|System::String ^|marshal_as|Marshal.h|  
|wchar_t \*|System::String ^|marshal_as|Marshal.h|  
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
  
 Marshaling de requiert un contexte uniquement lorsque marshaler les types de données managées au mode natif et que vous convertissez en type natif n’a pas d’un destructeur pour automatique de nettoyage. Le contexte de marshaling détruit le type de données native allouées dans son destructeur. Par conséquent, les conversions qui requièrent un contexte sera valides uniquement jusqu'à ce que le contexte est supprimé. Pour enregistrer toutes les valeurs marshalés, vous devez copier les valeurs dans vos propres variables.  
  
> [!NOTE]
>  Si vous avez incorporé `NULL`s dans votre chaîne, le résultat du marshaling de la chaîne n’est pas garanti. Le texte incorporé `NULL`s peut entraîner la chaîne à tronquer ou ils peuvent être conservées.  
  
Cet exemple montre comment inclure le répertoire msclr dans une déclaration d’en-tête include :  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 La bibliothèque de marshaling est extensible afin que vous pouvez ajouter vos propres types de marshaling. Pour plus d’informations sur l’extension de la bibliothèque de marshaling, consultez [Comment : étendre la bibliothèque de Marshaling](../dotnet/how-to-extend-the-marshaling-library.md).  
  
 Dans les versions antérieures, vous pouvez marshaler des données à l’aide de [non managé](/dotnet/framework/interop/consuming-unmanaged-dll-functions). Pour plus d’informations sur `PInvoke`, consultez [appelant des fonctions natives à partir de Code managé](../dotnet/calling-native-functions-from-managed-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque de prise en charge C++](../dotnet/cpp-support-library.md)   
 [Guide pratique pour étendre la bibliothèque de marshaling](../dotnet/how-to-extend-the-marshaling-library.md)
