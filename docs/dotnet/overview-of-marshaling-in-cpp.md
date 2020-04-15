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
ms.openlocfilehash: 0c7bf18fa823c6301a79c3f989efa73c9e8f628a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372008"
---
# <a name="overview-of-marshaling-in-ccli"></a>Aperçu du marshaling dans le CMD/CLI

En mode mixte, vous devez parfois rassembler vos données entre les types natifs et gérés. La *bibliothèque de marshaling* vous aide à marshal et convertir les données d’une manière simple.  La bibliothèque de marshaling se compose `marshal_context` d’un ensemble de fonctions et d’une classe qui effectuent le marshaling pour les types communs. La bibliothèque est définie dans ces en-têtes dans **l’annuaire inclus/msclr** pour votre édition Visual Studio :

|En-tête|Description|
|---------------|-----------------|
|marshal.h|`marshal_context`fonctions de marshaling sans contexte et sans contexte|
|marshal_atlh| Fonctions pour marshaling types ATL|
|marshal_cppstd.h|Fonctions pour le marshaling standard types C|
|marshal_windows.h|Fonctions pour marshaling types de Windows|

Le chemin par défaut pour le dossier **msclr** est quelque chose comme ceci en fonction de l’édition que vous avez et le numéro de construction:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Vous pouvez utiliser la bibliothèque de marshaling avec ou sans [une classe marshal_context](../dotnet/marshal-context-class.md). Certaines conversions nécessitent un contexte. D’autres conversions peuvent être implémentées à l’aide de la fonction [marshal_as.](../dotnet/marshal-as.md) Le tableau suivant énumère les conversions actuelles prises en charge, si elles nécessitent un contexte, et quel dossier marshal vous devez inclure:

|De type|Pour taper|Méthode maréchal|Inclure le fichier|
|---------------|-------------|--------------------|------------------|
|Système::String|const char \*|marshal_context|marshal.h|
|const char \*|Système::String|marshal_as|marshal.h|
|char\*|Système::String|marshal_as|marshal.h|
|Système::String|const wchar_t\*|marshal_context|marshal.h|
|const wchar_t \*|Système::String|marshal_as|marshal.h|
|wchar_t \*|Système::String|marshal_as|marshal.h|
|Système::IntPtr|HANDLE|marshal_as|marshal_windows.h|
|HANDLE|Système::IntPtr|marshal_as|marshal_windows.h|
|Système::String|BSTR|marshal_context|marshal_windows.h|
|BSTR|Système::String|marshal_as|marshal.h|
|Système::String|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|Système::String|marshal_as|marshal_windows.h|
|Système::String|std::corde|marshal_as|marshal_cppstd.h|
|std::corde|Système::String|marshal_as|marshal_cppstd.h|
|Système::String|std::wstring|marshal_as|marshal_cppstd.h|
|std::wstring|Système::String|marshal_as|marshal_cppstd.h|
|Système::String|CStringT\<char>|marshal_as|marshal_atlh|
|CStringT\<char>|Système::String|marshal_as|marshal_atlh|
|Système::String|<wchar_t CStringT>|marshal_as|marshal_atlh|
|<wchar_t CStringT>|Système::String|marshal_as|marshal_atlh|
|Système::String|CComBSTR|marshal_as|marshal_atlh|
|CComBSTR|Système::String|marshal_as|marshal_atlh|

Le marshaling exige un contexte seulement lorsque vous marshal de gestion aux types de données indigènes et le type natif que vous convertissez à n’a pas un destructeur pour le nettoyage automatique. Le contexte de marshaling détruit le type de données indigène attribué dans son destructeur. Par conséquent, les conversions qui nécessitent un contexte ne seront valides que jusqu’à ce que le contexte soit supprimé. Pour enregistrer les valeurs marshalées, vous devez copier les valeurs de vos propres variables.

> [!NOTE]
> Si vous `NULL`avez intégré s dans votre chaîne, le résultat de la marshaling la chaîne n’est pas garanti. Le `NULL`s intégré peut faire tronquer la ficelle ou ils peuvent être conservés.

Cet exemple montre comment inclure le répertoire msclr dans une déclaration d’en-tête comprennent:

`#include "msclr\marshal_cppstd.h"`

La bibliothèque de marshaling est extensible afin que vous puissiez ajouter vos propres types de marshaling. Pour plus d’informations sur l’extension de la bibliothèque de marshaling, voir [Comment: Étendre la bibliothèque de marshaling](../dotnet/how-to-extend-the-marshaling-library.md).

## <a name="see-also"></a>Voir aussi

[bibliothèque de prise en charge C++](../dotnet/cpp-support-library.md)<br/>
[Comment : étendre la bibliothèque de marshaling](../dotnet/how-to-extend-the-marshaling-library.md)
