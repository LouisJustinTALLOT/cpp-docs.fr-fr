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
ms.openlocfilehash: 0cdd5db4fae8d9167fa9ab1aeb6a4e8cbfe76ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372510"
---
# <a name="calling-native-functions-from-managed-code"></a>Appel à des fonctions natives à partir de code managé

L’heure courante de fonctionnement de la langue fournit des services d’invocation de plate-forme, ou PInvoke, qui permet au code géré d’appeler des fonctions de type C dans les bibliothèques dynamiques natives (DLL). Le même marshaling de données est utilisé comme pour l’interopérabilité COM avec le temps d’exécution et pour le "It Just Works," ou IJW, mécanisme.

Pour plus d'informations, consultez les pages suivantes :

- [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Utilisation de l'interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Les échantillons de cette `PInvoke` section illustrent simplement comment peut être utilisé. `PInvoke`peut simplifier le marshaling personnalisé des données parce que vous fournissez des informations de marshaling déclarativement dans les attributs au lieu d’écrire le code de marshaling procédural.

> [!NOTE]
> La bibliothèque de marshaling offre une autre façon de rassembler les données entre les environnements autochtones et gérés d’une manière optimisée. Voir [Aperçu de marshaling in CMD](../dotnet/overview-of-marshaling-in-cpp.md) pour plus d’informations sur la bibliothèque de marshaling. La bibliothèque de marshaling est utilisable pour les données seulement, et non pour les fonctions.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke et l’attribut DllImport

L’exemple suivant montre `PInvoke` l’utilisation d’un programme Visual CMD. La fonction native met est définie dans msvcrt.dll. L’attribut DllImport est utilisé pour la déclaration des met.

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

L’échantillon suivant est équivalent à l’échantillon précédent, mais utilise IJW.

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

### <a name="advantages-of-ijw"></a>Avantages de l’IJW

- Il n’est `DLLImport` pas nécessaire d’écrire des déclarations d’attribut pour les API non gestions que le programme utilise. Il suffit d’inclure le fichier d’en-tête et le lien avec la bibliothèque d’importation.

- Le mécanisme IJW est légèrement plus rapide (par exemple, les talons IJW n’ont pas besoin de vérifier la nécessité d’épingler ou de copier des éléments de données parce que cela est fait explicitement par le développeur).

- Il illustre clairement les problèmes de rendement. Dans ce cas, le fait que vous traduisiez d’une chaîne Unicode à une chaîne ANSI et que vous avez une allocation de mémoire et une répartition des dossiers. Dans ce cas, un développeur qui écrit le `_putws` code `PtrToStringChars` à l’aide d’IJW se rendrait compte que l’appel et l’utilisation seraient meilleurs pour les performances.

- Si vous appelez de nombreuses API non gestions en utilisant les mêmes données, les mobiliser une fois et passer la copie maréchale est beaucoup plus efficace que de re-marshaling à chaque fois.

### <a name="disadvantages-of-ijw"></a>Inconvénients de l’IJW

- Le marshaling doit être spécifié explicitement dans le code plutôt que par des attributs (qui ont souvent des défauts appropriés).

- Le code de marshaling est en ligne, où il est plus envahissant dans le flux de la logique d’application.

- Parce que les types `IntPtr` explicites de retour des API pour la portabilité 32 bits à 64 bits, vous devez utiliser des appels supplémentaires. `ToPointer`

La méthode spécifique exposée par le C est la méthode la plus efficace et la plus explicite, au prix d’une complexité supplémentaire.

Si l’application utilise principalement des types de données non mentés ou si elle appelle plus d’API non gestion que les API cadre .NET, nous vous recommandons d’utiliser la fonctionnalité IJW. Pour appeler une API occasionnellement non gérée dans une application principalement gérée, le choix est plus subtil.

## <a name="pinvoke-with-windows-apis"></a>PInvoke avec API Windows

PInvoke est pratique pour les fonctions d’appel dans Windows.

Dans cet exemple, un programme Visual CMD s’interopère avec la fonction MessageBox qui fait partie de l’API Win32.

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

La sortie est une boîte de message qui a le titre PInvoke Test et contient le texte Bonjour Monde!.

L’information de marshaling est également utilisée par PInvoke pour rechercher des fonctions dans le DLL. Dans user32.dll il n’y a en fait pas de fonction MessageBox, mais CharSet-CharSet::Ansi permet à PInvoke d’utiliser MessageBoxA, la version ANSI, au lieu de MessageBoxW, qui est la version Unicode. En général, nous vous recommandons d’utiliser des versions Unicode d’API non galécées, car cela élimine les frais généraux de traduction du format unicode natif des objets à chaîne cadre .NET à ANSI.

## <a name="when-not-to-use-pinvoke"></a>Quand ne pas utiliser PInvoke

L’utilisation de PInvoke n’est pas appropriée pour toutes les fonctions de style C dans les LPL. Supposons, par exemple, qu’il y ait une fonction MakeSpecial dans mylib.dll déclarée comme suit :

`char * MakeSpecial(char * pszString);`

Si nous utilisons PInvoke dans une application Visual CMD, nous pourrions écrire quelque chose de similaire à ce qui suit :

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

La difficulté ici est que nous ne pouvons pas supprimer la mémoire pour la chaîne non gestion retournée par MakeSpecial. D’autres fonctions appelées par PInvoke renvoient un pointeur à un tampon interne qui n’a pas à être deallocated par l’utilisateur. Dans ce cas, l’utilisation de la fonctionnalité IJW est le choix évident.

## <a name="limitations-of-pinvoke"></a>Limitations de PInvoke

Vous ne pouvez pas retourner le même pointeur exact d’une fonction autochtone que vous avez pris comme paramètre. Si une fonction autochtone renvoie le pointeur qui lui a été marshaled par PInvoke, la corruption de mémoire et les exceptions peuvent s’ensuivre.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

L’échantillon suivant présente ce problème, et même si le programme peut sembler donner la bonne sortie, la sortie provient de la mémoire qui avait été libérée.

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

## <a name="marshaling-arguments"></a>Marshaling Arguments

Avec `PInvoke`, aucun marshaling n’est nécessaire entre les types primitifs gérés et natifs de Cô avec la même forme. Par exemple, aucun marshaling n’est nécessaire entre Int32 et int, ou entre Double et double.

Cependant, vous devez marshal types qui n’ont pas la même forme. Cela comprend les types d’omble, de ficelle et de struct. Le tableau suivant montre les cartes utilisées par le maréchal pour différents types :

|wtypes.h wtypes.h|Visual C++|C visuel avec /clr|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|Vide\*|Vide\*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|SHORT|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|nombre entier non signé|nombre entier non signé|UInt32|
|LONG|long|long|Int32|
|BOOL|long|bool|Boolean|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|CHAR|char|char|Char|
|LPSTR|char\*|Chaîne [in], StringBuilder [in, out]|Chaîne [in], StringBuilder [in, out]|
|LPCSTR|const char \*|Corde|String|
|LPWSTR|wchar_t \*|Chaîne [in], StringBuilder [in, out]|Chaîne [in], StringBuilder [in, out]|
|LPCWSTR|const wchar_t \*|Corde|String|
|FLOAT|float|float|Unique|
|DOUBLE|double|double|Double|

Le maréchal épingle automatiquement la mémoire allouée sur le tas de temps de fonctionnement si son adresse est passée à une fonction non gérée. L’épinglage empêche le éboueur de déplacer le bloc de mémoire alloué pendant le compactage.

Dans l’exemple présenté plus tôt dans ce sujet, le paramètre CharSet de DllImport précise comment les cordes gérées doivent être mobilisées; dans ce cas, ils devraient être marshaled aux cordes ansI pour le côté indigène.

Vous pouvez spécifier des informations de mise en candidature pour les arguments individuels d’une fonction autochtone en utilisant l’attribut MarshalAs. Il y a plusieurs choix \* pour mobiliser un argument de corde : BStr, ANSIBStr, TBStr, LPStr, LPWStr, et LPTStr. La valeur par défaut est LPStr.

Dans cet exemple, la chaîne est marshaled comme une chaîne de caractère Unicode double-byte, LPWStr. La sortie est la première lettre de Hello World! parce que le deuxième byte de la corde maréchale est nul, et met interprète cela comme le marqueur de fin de chaîne.

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

L’attribut MarshalAs est dans le système::Runtime::InteropServices namespace. L’attribut peut être utilisé avec d’autres types de données tels que les tableaux.

Comme mentionné précédemment dans le sujet, la bibliothèque de marshaling fournit une nouvelle méthode optimisée de marshaling données entre les environnements autochtones et gérés. Pour plus d’informations, voir [Aperçu de l’enchôdre dans C .](../dotnet/overview-of-marshaling-in-cpp.md)

## <a name="performance-considerations"></a>Considérations relatives aux performances

PInvoke a une surcharge de 10 à 30 x86 instructions par appel. En plus de ce coût fixe, le marshaling crée des frais généraux supplémentaires. Il n’y a pas de coût de marshaling entre les types blittables qui ont la même représentation dans le code géré et non géré. Par exemple, il n’y a aucun coût à traduire entre int et Int32.

Pour de meilleures performances, avoir moins d’appels PInvoke qui marshal autant de données que possible, au lieu de plus d’appels qui marshal moins de données par appel.

## <a name="see-also"></a>Voir aussi

[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)
