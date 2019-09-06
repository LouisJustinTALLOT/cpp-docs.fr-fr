---
title: Vue d’ensemble du marshaling dans C++
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 937fbdf4b3ed09344e69a8f1eb731565c36794ae
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "70311777"
---
# <a name="overview-of-marshaling-in-ccli"></a>Vue d’ensemble du marshaling dans C++/CLI

En mode mixte, vous devez parfois marshaler vos données entre les types natifs et managés. La *bibliothèque de marshaling* vous permet de marshaler et de convertir les données d’une manière simple.  La bibliothèque de marshaling se compose d’un ensemble de fonctions `marshal_context` et d’une classe qui effectue le marshaling pour les types courants. La bibliothèque est définie dans ces en-têtes dans le répertoire **include/msclr,** pour votre édition de Visual Studio :

|Header|Description|
|---------------|-----------------|
|Marshal. h|`marshal_context`fonctions de marshaling sans contexte et de classe|
|marshal_atl.h| Fonctions de marshaling des types ATL|
|marshal_cppstd.h|Fonctions de marshaling des C++ types standard|
|marshal_windows.h|Fonctions pour le marshaling des types Windows|

Le chemin d’accès par défaut pour le dossier **msclr,** est semblable à celui-ci en fonction de l’édition dont vous disposez et du numéro de build :

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Vous pouvez utiliser la bibliothèque de marshaling avec ou sans [classe marshal_context](../dotnet/marshal-context-class.md). Certaines conversions requièrent un contexte. D’autres conversions peuvent être implémentées à l’aide de la fonction [marshal_as](../dotnet/marshal-as.md) . Le tableau suivant répertorie les conversions actuellement prises en charge, si elles nécessitent un contexte et le fichier Marshal que vous devez inclure :

|À partir du type|Pour taper|Méthode Marshal|Fichier include|
|---------------|-------------|--------------------|------------------|
|System::String^|const char\*|marshal_context|Marshal. h|
|const char\*|System::String^|marshal_as|Marshal. h|
|Char\*|System::String^|marshal_as|Marshal. h|
|System::String^|const wchar_t\*|marshal_context|Marshal. h|
|const wchar_t\*|System::String^|marshal_as|Marshal. h|
|wchar_t\*|System::String^|marshal_as|Marshal. h|
|System::IntPtr|HANDLE|marshal_as|marshal_windows.h|
|HANDLE|System::IntPtr|marshal_as|marshal_windows.h|
|System::String^|BSTR|marshal_context|marshal_windows.h|
|BSTR|System::String^|marshal_as|Marshal. h|
|System::String^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|System::String^|marshal_as|marshal_windows.h|
|System::String^|std::string|marshal_as|marshal_cppstd.h|
|std::string|System::String^|marshal_as|marshal_cppstd.h|
|System::String^|std::wstring|marshal_as|marshal_cppstd.h|
|std::wstring|System::String^|marshal_as|marshal_cppstd.h|
|System::String^|CStringT\<char>|marshal_as|marshal_atl.h|
|CStringT\<char>|System::String^|marshal_as|marshal_atl.h|
|System::String^|CStringT<wchar_t>|marshal_as|marshal_atl.h|
|CStringT<wchar_t>|System::String^|marshal_as|marshal_atl.h|
|System::String^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|System::String^|marshal_as|marshal_atl.h|

Le marshaling requiert un contexte uniquement lorsque vous effectuez un marshaling à partir de types de données managés en natif et que le type natif vers lequel vous effectuez la conversion n’a pas de destructeur pour le nettoyage automatique. Le contexte de marshaling détruit le type de données natif alloué dans son destructeur. Par conséquent, les conversions qui requièrent un contexte sont valides uniquement jusqu’à la suppression du contexte. Pour enregistrer des valeurs marshalées, vous devez les copier dans vos propres variables.

> [!NOTE]
>  Si vous avez incorporé `NULL`des dans votre chaîne, le résultat du marshaling de la chaîne n’est pas garanti. Les s `NULL`incorporés peuvent entraîner la troncation de la chaîne ou la conservation de ces dernières.

Cet exemple montre comment inclure le répertoire msclr, dans une déclaration d’en-tête include :

`#include "msclr\marshal_cppstd.h"`

La bibliothèque de marshaling est extensible afin que vous puissiez ajouter vos propres types de marshaling. Pour plus d’informations sur l’extension de la bibliothèque de [marshaling, consultez Procédure : Étendre la bibliothèque](../dotnet/how-to-extend-the-marshaling-library.md)de marshaling.

## <a name="see-also"></a>Voir aussi

[Bibliothèque de prise en charge C++](../dotnet/cpp-support-library.md)<br/>
[Guide pratique pour étendre la bibliothèque de marshaling](../dotnet/how-to-extend-the-marshaling-library.md)
