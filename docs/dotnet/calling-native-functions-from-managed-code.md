---
title: Appeler des fonctions natives à partir du Code managé | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f3b8b266d44f9109a346160a1b2493f8644be839
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207596"
---
# <a name="calling-native-functions-from-managed-code"></a>Appel à des fonctions natives à partir de code managé
Le common language runtime fournit des Services d’appel de plateforme, ou PInvoke, qui permet au code managé appelle des fonctions de style C dans les bibliothèques dynamiques liées (DLL) natives. Les même marshaling de données sont utilisées que pour l’interopérabilité COM avec le runtime et pour le « It Just Works », mécanisme IJW.  
  
 Pour plus d'informations, voir :  
  
-   [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Présentation détaillée de l’appel de code non managé](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 Les exemples de cette section illustrent simplement comment `PInvoke` peut être utilisé. `PInvoke` peut simplifier le marshaling de données personnalisées parce que vous fournissez des informations de marshaling façon déclarative dans les attributs au lieu d’écrire le code de marshaling procédural.  
  
> [!NOTE]
>  La bibliothèque de marshaling fournit une autre façon de marshaler les données entre les environnements natifs et managés de manière optimisée. Consultez [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md) pour plus d’informations sur la bibliothèque de marshaling. La bibliothèque de marshaling est utilisable uniquement pour les données et pas pour les fonctions.  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke et l’attribut DllImport  
 L’exemple suivant illustre l’utilisation de `PInvoke` dans un programme Visual C++. La fonction native puts est défini dans msvcrt.dll. L’attribut DllImport est utilisé pour la déclaration de puts.  
  
```  
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
  
```  
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
  
-   Il est inutile d’écrire `DLLImport` déclarations pour les API non managées utilisées par le programme d’attribut. Simplement inclure le fichier d’en-tête et un lien avec la bibliothèque d’importation.  
  
-   Le mécanisme IJW est légèrement plus rapide (par exemple, les stubs IJW n’avez pas besoin de vérifier la nécessité d’épingler ou copier des éléments de données, qui est fait explicitement par le développeur).  
  
-   Elle illustre clairement les problèmes de performances. Dans ce cas, le fait que vous traduisiez une chaîne Unicode en une chaîne ANSI et que vous avez une allocation de mémoire et la désallocation. Dans ce cas, un développeur écrivant le code à l’aide de IJW rendrait compte qu’appeler `_putws` et à l’aide de `PtrToStringChars` serait préférable pour les performances.  
  
-   Si vous appelez des nombreuses API non managées utilisant les mêmes données, marshaler une fois et en passant la copie marshalée est beaucoup plus efficace que de remarshaler chaque fois.  
  
### <a name="disadvantages-of-ijw"></a>Inconvénients de IJW  
  
-   Marshaling doit être spécifié explicitement dans le code au lieu de par les attributs (lesquels ont souvent des valeurs par défaut appropriées).  
  
-   Le code de marshaling est inline, où il est plus envahissant dans le flux de la logique d’application.  
  
-   Étant donné que les API de marshaling explicites retournent `IntPtr` types de portabilité 32 bits vers 64 bits, vous devez utiliser très `ToPointer` appels.  
  
 La méthode spécifique exposée par C++ est la méthode plus efficace, explicite, au prix d’une complexité supplémentaire.  
  
 Si l’application utilise principalement des types de données non managés ou si elle appelle davantage d’API non managées que les API .NET Framework, nous recommandons que vous utilisez la fonctionnalité IJW. Pour appeler une API non managée occasionnelle dans une application essentiellement managée, le choix est plus subtil.  
  
## <a name="pinvoke-with-windows-apis"></a>PInvoke avec les API Windows  
 PInvoke est pratique pour appeler des fonctions dans Windows.  
  
 Dans cet exemple, un programme Visual C++ interagit avec la fonction MessageBox qui fait partie de l’API Win32.  
  
```  
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
  
 La sortie est une boîte de message dispose le titre PInvoke Test qui contient le texte Hello World !.  
  
 Les informations de marshaling sont également utilisées par PInvoke pour rechercher des fonctions dans la DLL. Dans user32.dll en ne fait, aucune fonction MessageBox, mais CharSet = CharSet :: ANSI permet à PInvoke d’utiliser MessageBoxA, la version ANSI, au lieu de MessageBoxW, qui est la version Unicode. En règle générale, nous vous recommandons d’utiliser les versions Unicode d’API non managées, car cela élimine la traduction à partir d’une surcharge au format Unicode natif d’objets chaîne .NET Framework en ANSI.  
  
## <a name="when-not-to-use-pinvoke"></a>Quand ne pas utiliser PInvoke  
 À l’aide de PInvoke n’est pas appropriée pour toutes les fonctions de style C dans les DLL. Par exemple, supposons qu’il est une fonction MakeSpecial dans mylib.dll déclarée comme suit :  
  
 `char * MakeSpecial(char * pszString);`  
  
 Si nous utilisons PInvoke dans une application Visual C++, nous pouvons écrire quelque chose de similaire à ce qui suit :  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 La difficulté, ici est que nous ne pouvons pas supprimer la mémoire pour la chaîne non managée retournée par MakeSpecial. Autres fonctions appelées via PInvoke retournent un pointeur vers une mémoire tampon interne qui n’a pas d’être libérée par l’utilisateur. Dans ce cas, à l’aide de la fonctionnalité IJW est le choix évident.  
  
## <a name="limitations-of-pinvoke"></a>Limitations de PInvoke  
 Vous ne pouvez pas retourner exactement le même pointeur à partir d’une fonction native que vous avez suivies en tant que paramètre. Si une fonction native retourne le pointeur qui a été marshalé à celui-ci par PInvoke, exceptions et la corruption de la mémoire peuvent survenir.  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 L’exemple suivant illustre ce problème, et bien que le programme puisse paraître donner la sortie correcte, la sortie sera disponible à partir de la mémoire libérée au préalable.  
  
```  
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
  
## <a name="marshaling-arguments"></a>Marshaling des Arguments  
 Avec `PInvoke`, aucun marshaling n’est nécessaire entre managed C++ natif des types primitifs ou avec le même formulaire. Par exemple, aucun marshaling n’est requis entre Int32 et int, ou entre Double et double.  
  
 Toutefois, vous devez marshaler les types qui n’ont pas la même forme. Cela inclut les types char, string et struct. Le tableau suivant montre les mappages utilisés par le marshaleur pour différents types :  
  
|Wtypes.h|Visual C++|Visual C++ avec /clr|Common Language Runtime|  
|--------------|------------------|-----------------------------|-----------------------------|  
|HANDLE|Void \*|Void \*|IntPtr, UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|SHORT|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|INT|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|LONG|long|long|Int32|  
|BOOL|long|bool|Booléen|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG|unsigned long|unsigned long|UInt32|  
|CHAR|char|char|Char|  
|LPCSTR|Char \*|String ^ [in], StringBuilder ^ [dans, out]|String ^ [in], StringBuilder ^ [dans, out]|  
|LPCSTR|const char \*|String ^|Chaîne|  
|LPWSTR|wchar_t \*|String ^ [in], StringBuilder ^ [dans, out]|String ^ [in], StringBuilder ^ [dans, out]|  
|LPCWSTR|wchar_t const \*|String ^|Chaîne|  
|FLOAT|float|float|Single|  
|DOUBLE|double|double|Double|  
  
 Le marshaleur épingle automatiquement la mémoire allouée sur le tas du runtime si son adresse est passée à une fonction non managée. L’épinglage empêche le garbage collector de déplacer le bloc de mémoire alloué pendant le compactage.  
  
 Dans l’exemple présenté plus haut dans cette rubrique, le paramètre CharSet de DllImport spécifie comment les chaînes managées doivent être marshalées ; Dans ce cas, ils doivent être marshalées vers des chaînes ANSI pour le côté natif.  
  
 Vous pouvez spécifier des informations de marshaling pour les arguments individuels d’une fonction native à l’aide de l’attribut MarshalAs. Il existe plusieurs choix pour marshaler une chaîne \* argument : BStr, ANSIBStr, TBStr, LPStr, LPWStr et LPTStr. La valeur par défaut est LPStr.  
  
 Dans cet exemple, la chaîne est marshalée comme une chaîne de caractères Unicode sur deux octets, LPWStr. La sortie est la première lettre de Hello World ! Étant donné que le deuxième octet de la chaîne marshalée est null et place l’interprète comme marqueur de fin de chaîne.  
  
```  
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
  
 L’attribut MarshalAs se trouve dans l’espace de noms System::Runtime :: InteropServices. L’attribut peut être utilisé avec d’autres types de données tels que des tableaux.  
  
 Comme mentionné précédemment dans la rubrique, la bibliothèque de marshaling fournit une méthode nouvelle et optimisée du marshaling des données entre les environnements natifs et managés. Pour plus d’informations, consultez [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
## <a name="performance-considerations"></a>Considérations sur les performances  
 PInvoke a une surcharge d’entre 10 et 30 x86 instructions par appel. En plus de ce coût fixe, le marshaling crée supplémentaire surcharge. Il n’existe aucun coût de marshaling entre les types blittables ayant la même représentation dans le code managé et non managé. Par exemple, il n’existe aucun coût pour traduire d’int à Int32.  
  
 Pour de meilleures performances, ont moins d’appels PInvoke qui marshalent autant de données que possible, plutôt que davantage d’appels qui marshalent moins de données par appel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)