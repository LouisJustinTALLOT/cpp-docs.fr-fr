---
title: Appel à des fonctions natives à partir de code managé
ms.date: 11/04/2016
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
ms.openlocfilehash: 50f40cc147daaa26a7fa4e607f0d4dd42cf22d61
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988667"
---
# <a name="calling-native-functions-from-managed-code"></a>Appel à des fonctions natives à partir de code managé

Le Common Language Runtime fournit des services d'appel de code non managé (Platform Invocation Services), ou PInvoke, qui permettent au code managé d'appeler des fonctions de style C dans les bibliothèques dynamiques liées (DLL) natives. Le même marshaling de données est utilisé de la même façon que pour l'interopérabilité COM avec le runtime, ainsi que pour le mécanisme IJW (« It Just Works »).

Pour plus d'informations, consultez .

- [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Les exemples de cette section illustrent simplement l'utilisation de `PInvoke`. `PInvoke` peut simplifier le marshaling de données personnalisées parce que vous fournissez de façon déclarative les informations de marshaling dans les attributs au lieu d'écrire le code de marshaling procédural.

> [!NOTE]
>  La bibliothèque de marshaling offre une autre manière de marshaler les données entre les environnements managés et les environnements natifs d'une manière optimisée. Pour plus d’informations sur la bibliothèque de marshaling [, consultez vue d’ensemble du C++ marshaling dans](../dotnet/overview-of-marshaling-in-cpp.md) . La bibliothèque de marshaling est utilisable uniquement pour les données, pas pour les fonctions.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke et l'attribut DllImport

L'exemple suivant montre comment utiliser `PInvoke` dans un programme Visual C++. La fonction native puts est défini dans msvcrt.dll. L'attribut DllImport est utilisé pour la déclaration de puts.

```cpp
// platform_invocation_services.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", CharSet=CharSet::Ansi)]
extern "C" int puts(String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

L'exemple suivant est équivalent au précédent, mais utilise IJW.

```cpp
// platform_invocation_services_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#include <stdio.h>

int main() {
   String ^ pStr = "Hello World!";
   char* pChars = (char*)Marshal::StringToHGlobalAnsi(pStr).ToPointer();
   puts(pChars);

   Marshal::FreeHGlobal((IntPtr)pChars);
}
```

### <a name="advantages-of-ijw"></a>Avantages de IJW

- Il n'est pas nécessaire d'écrire des déclarations attribute `DLLImport` pour les API non managées utilisées par le programme. Il suffit d'inclure le fichier d'en-tête et d'effectuer une liaison avec la bibliothèque d'importation.

- Le mécanisme IJW est légèrement plus rapide (par exemple, les stubs IJW n'ont pas besoin de vérifier la nécessité d'épingler ou de copier des éléments de données car le développeur s'en charge explicitement).

- Il fait clairement apparaître les problèmes de performance. Ici, le fait que vous traduisiez une chaîne Unicode en une chaîne ANSI et que vous ayez une allocation et une désallocation de mémoire correspondante. Dans ce cas, un développeur écrivant le code à l'aide de IJW se rendrait compte qu'appeler `_putws` et utiliser `PtrToStringChars` serait plus rentable en termes de performances.

- Si vous appelez un grand nombre d'API non managées utilisant les mêmes données, les marshaler une fois pour toutes au départ et faire circuler la copie marshalée est beaucoup plus efficace que de remarshaler chaque fois.

### <a name="disadvantages-of-ijw"></a>Inconvénients de IJW

- Le Marshaling doit être spécifié explicitement dans le code plutôt que par les attributs (lesquels ont souvent des valeurs par défaut appropriées).

- Le code de marshaling est inline, où il est plus envahissant dans le flux de la logique de l'application.

- Comme les API de marshaling explicites retournent des types `IntPtr` pour des raisons de portabilité 32 bits vers 64 bits, il faut utiliser des appels `ToPointer` supplémentaires.

La méthode spécifique exposée par C++ est la méthode la plus efficace et la plus explicite, ce qui se paye par un peu plus de complexité.

Si l'application utilise principalement des types de données non managés ou si elle appelle davantage d'API non managées que d'API .NET Framework, il sera généralement préférable d'utiliser la fonctionnalité IJW. Pour appeler une API non managée occasionnelle dans une application essentiellement managée, le choix est plus délicat.

## <a name="pinvoke-with-windows-apis"></a>PInvoke avec les API Windows

PInvoke est pratique pour appeler des fonctions dans Windows.

Dans cet exemple, un programme Visual C++ interagit avec la fonction MessageBox qui fait partie de l'API Win32.

```cpp
// platform_invocation_services_4.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
typedef void* HWND;
[DllImport("user32", CharSet=CharSet::Ansi)]
extern "C" int MessageBox(HWND hWnd, String ^ pText, String ^ pCaption, unsigned int uType);

int main() {
   String ^ pText = "Hello World! ";
   String ^ pCaption = "PInvoke Test";
   MessageBox(0, pText, pCaption, 0);
}
```

La sortie est une boîte de message dont le titre PInvoke Test contient le texte Hello World!.

Les informations de marshaling sont également utilisées par PInvoke pour rechercher des fonctions dans la DLL. Dans user32.dll, il n'y a en réalité aucune fonction MessageBox, mais CharSet=CharSet::Ansi permet à PInvoke d'utiliser MessageBoxA, la version ANSI, au lieu de MessageBoxW, qui est la version Unicode. En général, nous vous conseillons d'utiliser des versions Unicode d'API non managées, car cela élimine les charges mémoire dues à la traduction d'objets chaîne .NET Framework depuis le format Unicode natif en ANSI.

## <a name="when-not-to-use-pinvoke"></a>Quand ne pas utiliser PInvoke

L'utilisation de PInvoke n'est pas appropriée pour toutes les fonctions de style C dans les DLL. Par exemple, supposons une fonction MakeSpecial dans mylib.dll, déclarée comme suit :

`char * MakeSpecial(char * pszString);`

Si nous utilisons PInvoke dans une application Visual C++, nous pouvons écrire quelque chose de semblable à ce qui suit :

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

La difficulté, ici, est que nous ne pouvons pas supprimer la mémoire de la chaîne non managée retournée par MakeSpecial. D'autres fonctions appelées par le biais de PInvoke retournent un pointeur vers une mémoire tampon interne qui n'a pas besoin d'être libérée par l'utilisateur. Dans ce cas, la fonctionnalité IJW est le choix qui s'impose.

## <a name="limitations-of-pinvoke"></a>Limitations de PInvoke

Vous ne pouvez pas retourner exactement le même pointeur d'une fonction native que celui que vous avez pris comme paramètre. Si une fonction native retourne le pointeur qui lui a été marshalé par PInvoke, des problèmes d'altération de la mémoire et des exceptions peuvent survenir.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

L'exemple suivant illustre ce problème, et bien que le programme puisse paraître donner la sortie correcte, celle-ci provient d'une mémoire libérée au préalable.

```cpp
// platform_invocation_services_5.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
#include <limits.h>

ref struct MyPInvokeWrap {
public:
   [ DllImport("user32.dll", EntryPoint = "CharLower", CharSet = CharSet::Ansi) ]
   static String^ CharLower([In, Out] String ^);
};

int main() {
   String ^ strout = "AabCc";
   Console::WriteLine(strout);
   strout = MyPInvokeWrap::CharLower(strout);
   Console::WriteLine(strout);
}
```

## <a name="marshaling-arguments"></a>Marshaler des arguments

Avec `PInvoke`, aucun marshaling n'est nécessaire entre des types primitifs natifs managés ou C++ de même format. Par exemple, aucun marshaling n'est requis entre Int32 et int, ou entre Double et double.

Toutefois, vous devez marshaler les types qui ont un format différent. Cela concerne les caractères, les chaînes et les types struct. Le tableau suivant montre les mappages utilisés par le marshaleur pour différents types :

|wtypes.h|Visual C++|Visual C++ avec /clr|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|void \*|void \*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|SHORT|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|unsigned int|unsigned int|UInt32|
|LONG|long|long|Int32|
|BOOL|long|bool|Boolean|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|CHAR|char|char|Char|
|LPCSTR|\* char|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|const char \*|String ^|String|
|LPWSTR|wchar_t \*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|\* wchar_t const|String ^|String|
|FLOAT|float|float|Single|
|DOUBLE|double|double|Double|

Le marshaleur épingle automatiquement la mémoire allouée sur le tas d'exécution si son adresse est passée à une fonction non managée. L'épinglage empêche le garbage collector de déplacer le bloc de mémoire alloué pendant le compactage.

Dans l'exemple montré plus haut dans cette rubrique, le paramètre CharSet de DllImport spécifie comment les chaînes managées doivent être marshalées ; dans ce cas, elles doivent être marshalées vers des chaînes ANSI pour le côté natif.

Vous pouvez spécifier des informations de marshaling pour les arguments individuels d'une fonction native à l'aide de l'attribut MarshalAs. Il existe plusieurs options pour marshaler une chaîne \* argument : BStr, ANSIBStr, TBStr, LPStr, LPWStr et LPTStr. La valeur par défaut est LPStr.

Dans cet exemple, la chaîne est marshalée comme une chaîne de caractères Unicode à double octet, LPWStr. La sortie est la première lettre de Hello World ! étant donné que le deuxième octet de la chaîne marshalée est null, et est interprété comme le marqueur de fin de chaîne.

```cpp
// platform_invocation_services_3.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", EntryPoint="puts")]
extern "C" int puts([MarshalAs(UnmanagedType::LPWStr)] String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

L'attribut MarshalAs se trouve dans l'espace de noms System::Runtime::InteropServices. Il peut être utilisé avec d'autres types de données tels que des tableaux.

Comme mentionné précédemment dans la rubrique, la bibliothèque de marshaling fournit une méthode nouvelle et optimisée pour marshaler les données entre les environnements managés et les environnements natifs. Pour plus d’informations, consultez [vue d’ensemble du C++marshaling dans ](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Considérations sur les performances

La charge mémoire de PInvoke se situe entre 10 et 30 instructions x86 par appel. En plus de ce coût fixe, le marshaling crée une charge mémoire supplémentaire. Il n'existe aucun coût de marshaling entre les types blittables ayant la même représentation en code managé et non managé. Par exemple, traduire de int à Int32 n'entraîne aucun coût.

Pour de meilleures performances, ayez un moins grand nombre d'appels PInvoke, mais qui marshalent autant de données que possible, plutôt que davantage d'appels qui marshalent moins de données par appel.

## <a name="see-also"></a>Voir aussi

[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)
