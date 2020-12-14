---
description: 'En savoir plus sur : Comment : marshaler des chaînes à l’aide de PInvoke'
title: "Comment : marshaler des chaînes à l'aide de PInvoke"
ms.custom: get-started-article
ms.date: 09/09/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: 29bec9a05d0425d1ce2cde42b89dacc7818ebac1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302567"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Comment : marshaler des chaînes à l'aide de PInvoke

Cette rubrique explique comment des fonctions natives qui acceptent des chaînes de style C peuvent être appelées à l’aide du type de chaîne CLR System :: String à l’aide de la prise en charge de l’appel de plateforme .NET Framework. Visual C++ les programmeurs sont encouragés à utiliser les fonctionnalités d’interopérabilité C++ à la place (dans la mesure du possible), car P/Invoke fournit peu de rapports d’erreurs de compilation, n’est pas de type sécurisé et peut être fastidieux à implémenter. Si l’API non managée est empaquetée en tant que DLL et que le code source n’est pas disponible, P/Invoke est la seule option, mais dans le cas contraire, consultez [utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Les chaînes managées et non managées sont présentées différemment en mémoire. par conséquent, le passage de chaînes de fonctions managées à des fonctions non managées requiert que l' <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut indique au compilateur d’insérer les mécanismes de conversion requis pour marshaler les données de chaîne correctement et en toute sécurité.

Comme avec les fonctions qui utilisent uniquement des types de données intrinsèques, <xref:System.Runtime.InteropServices.DllImportAttribute> est utilisé pour déclarer des points d’entrée managés dans les fonctions natives, mais--pour passer des chaînes--au lieu de définir ces points d’entrée comme prenant des chaînes de style C, un handle vers le <xref:System.String> type peut être utilisé à la place. Cela invite le compilateur à insérer le code qui effectue la conversion requise. Pour chaque argument de fonction dans une fonction non managée qui prend une chaîne, l' <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut doit être utilisé pour indiquer que l’objet String doit être marshalé vers la fonction native comme une chaîne de style C.

Le marshaleur encapsule l’appel à la fonction non managée dans une routine Wrapper cachée qui épingle et copie la chaîne managée dans une chaîne allouée localement dans le contexte non managé, qui est ensuite passé à la fonction non managée. Quand la fonction non managée retourne, le wrapper supprime la ressource ou, si elle se trouvait sur la pile, elle est récupérée lorsque le wrapper est hors de portée. La fonction non managée n’est pas responsable de cette mémoire. Le code non managé crée et supprime uniquement la mémoire dans le tas configuré par son propre CRT, donc il n’y a jamais de problème avec le marshaleur en utilisant une version CRT différente.

Si votre fonction non managée retourne une chaîne, sous la forme d’une valeur de retour ou d’un paramètre de sortie, le marshaleur la copie dans une nouvelle chaîne managée, puis libère la mémoire. Pour plus d’informations, consultez [comportement de marshaling par défaut](/dotnet/framework/interop/default-marshaling-behavior) et [marshaling de données à l’aide d’un appel de](/dotnet/framework/interop/marshaling-data-with-platform-invoke)code non managé.

## <a name="example"></a>Exemple

Le code suivant est constitué d’un module non managé et d’un module managé. Le module non managé est une DLL qui définit une fonction appelée TakesAString qui accepte une chaîne ANSI de style C sous la forme d’un caractère *. Le module managé est une application de ligne de commande qui importe la fonction TakesAString, mais la définit comme prenant un System. String managé au lieu d’un char \* . L' <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut est utilisé pour indiquer comment la chaîne managée doit être marshalée lorsque TakesAString est appelé.

```cpp
// TraditionalDll2.cpp
// compile with: /LD /EHsc
#include <windows.h>
#include <stdio.h>
#include <iostream>

using namespace std;

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAString(char*);
}

void TakesAString(char* p) {
   printf_s("[unmanaged] %s\n", p);
}
```

```cpp
// MarshalString.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL
{
   [DllImport("TraditionalDLL2.dll")]
      static public void
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);
};

int main() {
   String^ s = gcnew String("sample string");
    Console::WriteLine("[managed] passing managed string to unmanaged function...");
   TraditionalDLL::TakesAString(s);
   Console::WriteLine("[managed] {0}", s);
}
```

Cette technique entraîne la construction d’une copie de la chaîne sur le tas non managé. par conséquent, les modifications apportées à la chaîne par la fonction native ne seront pas reflétées dans la copie managée de la chaîne.

Notez qu’aucune partie de la DLL n’est exposée au code managé via la directive #include traditionnelle. En fait, la DLL est accessible uniquement au moment de l’exécution. par conséquent, les problèmes liés aux fonctions importées avec `DllImport` ne sont pas détectés au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
