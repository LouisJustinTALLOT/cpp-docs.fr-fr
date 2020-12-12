---
description: 'En savoir plus sur : appel de fonctions natives à partir de code managé'
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
ms.openlocfilehash: b037027f863ff12ac83429715cdf50bff4549a93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282534"
---
# <a name="calling-native-functions-from-managed-code"></a>Appel à des fonctions natives à partir de code managé

Le common language runtime fournit des services d’appel de code non managé, ou PInvoke, qui permet au code managé d’appeler des fonctions de style C dans les bibliothèques de liens dynamiques (dll) natives. Le même marshaling de données est utilisé comme pour l’interopérabilité COM avec le runtime et pour le mécanisme « It Just Works », ou IJW.

Pour plus d'informations, consultez les pages suivantes :

- [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Les exemples de cette section illustrent simplement la façon dont `PInvoke` peut être utilisé. `PInvoke` peut simplifier le marshaling des données personnalisées, car vous fournissez des informations de marshaling de façon déclarative dans des attributs au lieu d’écrire du code de marshaling procédural.

> [!NOTE]
> La bibliothèque de marshaling fournit un autre moyen de marshaler les données entre les environnements natifs et gérés de façon optimisée. Pour plus d’informations sur la bibliothèque de marshaling [, consultez vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md) . La bibliothèque de marshaling est utilisable uniquement pour les données, et non pour les fonctions.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke et l’attribut DllImport

L’exemple suivant illustre l’utilisation de `PInvoke` dans un programme Visual C++. La fonction native put est définie dans msvcrt.dll. L’attribut DllImport est utilisé pour la déclaration des put.

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

L’exemple suivant est équivalent à l’exemple précédent, mais utilise IJW.

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

- Il n’est pas nécessaire d’écrire `DLLImport` des déclarations d’attribut pour les API non managées utilisées par le programme. Incluez simplement le fichier d’en-tête et le lien avec la bibliothèque d’importation.

- Le mécanisme IJW est légèrement plus rapide (par exemple, les stubs IJW n’ont pas besoin de vérifier la nécessité d’épingler ou de copier des éléments de données, car ils sont effectués explicitement par le développeur).

- Il illustre clairement les problèmes de performances. Dans ce cas, le fait que vous traduisiez à partir d’une chaîne Unicode en une chaîne ANSI et que vous ayez une allocation et une désallocation de la mémoire du surveillant. Dans ce cas, un développeur écrivant le code à l’aide de IJW se rend compte que l’appel `_putws` et l’utilisation `PtrToStringChars` de seraient mieux adaptées aux performances.

- Si vous appelez de nombreuses API non managées à l’aide des mêmes données, le marshaling et le passage de la copie marshalée sont beaucoup plus efficaces que le remarshaling à chaque fois.

### <a name="disadvantages-of-ijw"></a>Inconvénients de IJW

- Le marshaling doit être spécifié explicitement dans le code plutôt que par les attributs (qui ont souvent des valeurs par défaut appropriées).

- Le code de marshaling est Inline, où il est plus invasif dans le déroulement de la logique d’application.

- Étant donné que les API de marshaling explicites retournent `IntPtr` des types pour la portabilité 32 bits vers 64 bits, vous devez utiliser des `ToPointer` appels supplémentaires.

La méthode spécifique exposée par C++ est la méthode plus efficace et explicite, au détriment d’une complexité supplémentaire.

Si l’application utilise principalement des types de données non managés ou si elle appelle des API non managées plutôt que des API .NET Framework, nous vous recommandons d’utiliser la fonctionnalité IJW. Pour appeler une API non managée occasionnelle dans une application principalement gérée, le choix est plus subtil.

## <a name="pinvoke-with-windows-apis"></a>PInvoke avec les API Windows

PInvoke est pratique pour appeler des fonctions dans Windows.

Dans cet exemple, un programme Visual C++ interagit avec la fonction MessageBox qui fait partie de l’API Win32.

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

La sortie est une boîte de message avec le titre PInvoke test et contenant le texte Hello World !.

Les informations de marshaling sont également utilisées par PInvoke pour rechercher des fonctions dans la DLL. En user32.dll il n’existe en fait aucune fonction MessageBox, mais CharSet = CharSet :: ANSI permet à PInvoke d’utiliser MessageBoxA, la version ANSI, au lieu de MessageBoxW, qui est la version Unicode. En général, nous vous recommandons d’utiliser des versions Unicode d’API non managées, car cela élimine la surcharge de traduction du format Unicode natif de .NET Framework objets de chaîne à ANSI.

## <a name="when-not-to-use-pinvoke"></a>Quand ne pas utiliser PInvoke

L’utilisation de PInvoke n’est pas appropriée pour toutes les fonctions de style C dans les dll. Par exemple, supposons qu’il existe une fonction MakeSpecial dans mylib.dll déclarée comme suit :

`char * MakeSpecial(char * pszString);`

Si nous utilisons PInvoke dans une application Visual C++, nous pouvons écrire un code similaire à ce qui suit :

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

La difficulté ici est que nous ne pouvons pas supprimer la mémoire pour la chaîne non managée retournée par MakeSpecial. D’autres fonctions appelées par le biais de PInvoke retournent un pointeur vers une mémoire tampon interne qui n’a pas besoin d’être libérée par l’utilisateur. Dans ce cas, l’utilisation de la fonctionnalité IJW est le choix évident.

## <a name="limitations-of-pinvoke"></a>Limitations de PInvoke

Vous ne pouvez pas retourner le même pointeur exact à partir d’une fonction native que vous avez pris comme paramètre. Si une fonction native retourne le pointeur qui lui a été marshalé par PInvoke, une altération de la mémoire et des exceptions peuvent être levées.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

L’exemple suivant présente ce problème, et même si le programme peut sembler donner la sortie correcte, la sortie provient de la mémoire qui avait été libérée.

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

## <a name="marshaling-arguments"></a>Marshaling des arguments

Avec `PInvoke` , aucun marshaling n’est nécessaire entre les types primitifs natifs managés et C++ ayant la même forme. Par exemple, aucun marshaling n’est requis entre Int32 et int, ou entre double et double.

Toutefois, vous devez marshaler les types qui n’ont pas le même formulaire. Cela comprend les types char, String et struct. Le tableau suivant montre les mappages utilisés par le marshaleur pour différents types :

|Wtypes. h|Visual C++|Visual C++ avec/CLR|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|nullité \*|nullité \*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|SHORT|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|nombre entier non signé|nombre entier non signé|UInt32|
|LONG|long|long|Int32|
|BOOL|long|bool|Booléen|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|CHAR|char|char|Char|
|LPSTR|Char \*|Chaîne ^ [in], StringBuilder ^ [in, out]|Chaîne ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|const char \*|Chaîne ^|Chaîne|
|LPWSTR|wchar_t \*|Chaîne ^ [in], StringBuilder ^ [in, out]|Chaîne ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|const wchar_t \*|Chaîne ^|Chaîne|
|FLOAT|float|float|Unique|
|DOUBLE|double|double|Double|

Le marshaleur épingle automatiquement la mémoire allouée sur le tas du Runtime si son adresse est passée à une fonction non managée. L’épinglage empêche le garbage collector de déplacer le bloc de mémoire alloué pendant le compactage.

Dans l’exemple présenté précédemment dans cette rubrique, le paramètre CharSet de DllImport spécifie la manière dont les chaînes managées doivent être marshalées ; dans ce cas, elles doivent être marshalées en chaînes ANSI pour le côté natif.

Vous pouvez spécifier des informations de marshaling pour les arguments individuels d’une fonction native à l’aide de l’attribut MarshalAs. Il existe plusieurs options pour marshaler un argument de chaîne \* : BSTR, AnsiBStr, TBStr, LPSTR, LPWStr et LPTStr. La valeur par défaut est LPStr.

Dans cet exemple, la chaîne est marshalée comme une chaîne de caractères Unicode sur deux octets, LPWStr. La sortie est la première lettre de Hello World ! étant donné que le deuxième octet de la chaîne marshalée est null, et est interprété comme le marqueur de fin de chaîne.

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

L’attribut MarshalAs se trouve dans l’espace de noms System :: Runtime :: InteropServices. L’attribut peut être utilisé avec d’autres types de données tels que des tableaux.

Comme mentionné plus haut dans la rubrique, la bibliothèque de marshaling fournit une nouvelle méthode optimisée de marshaling des données entre les environnements natifs et gérés. Pour plus d’informations, consultez [vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Considérations relatives aux performances

PInvoke a une surcharge qui est comprise entre 10 et 30 instructions x86 par appel. En plus de ce coût fixe, le marshaling crée une surcharge supplémentaire. Il n’y a aucun coût de marshaling entre les types blittables qui ont la même représentation dans du code managé et non managé. Par exemple, il n’y a aucun coût à traduire entre int et Int32.

Pour de meilleures performances, utilisez moins d’appels PInvoke qui marshalent autant de données que possible, plutôt que d’autres appels qui marshalent moins de données par appel.

## <a name="see-also"></a>Voir aussi

[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)
