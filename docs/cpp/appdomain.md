---
title: appdomain
ms.date: 11/04/2016
f1_keywords:
- appdomain_cpp
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
ms.openlocfilehash: 3f83841565eb6a097f306129fe8f6d121f837c27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184489"
---
# <a name="appdomain"></a>appdomain

Spécifie que chaque domaine d'application de votre application managée doit avoir sa propre copie d'une variable globale ou d'une variable membre static particulière. Consultez [domaines d’Application et Visual C++](../dotnet/application-domains-and-visual-cpp.md) pour plus d’informations.

Chaque domaine d'application a sa propre copie d'une variable par domaine d'application. Un constructeur d'une variable de domaine d'application est exécuté lorsqu'un assembly est chargé dans un domaine d'application, et le destructeur est exécuté lorsque le domaine d'application est déchargé.

Si vous voulez que tous les domaines d'application au sein d'un processus dans le Common Langage Runtime partagent une variable globale, utilisez le modificateur `__declspec(process)`. `__declspec(process)` est activé par défaut sous [/CLR](../build/reference/clr-common-language-runtime-compilation.md). Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

`__declspec(appdomain)` est valide uniquement lorsque une de la **/CLR** options du compilateur est utilisé. Seules une variable globale, une variable membre static ou une variable locale static peuvent être marquées avec `__declspec(appdomain)`. Il est incorrect d'appliquer `__declspec(appdomain)` aux membres static des types managés, car ils ont toujours ce comportement.

À l’aide de `__declspec(appdomain)` revient à utiliser [stockage Local des threads (TLS)](../parallel/thread-local-storage-tls.md). Les threads ont leur propre stockage, tout comme les domaines d'application. L'utilisation de `__declspec(appdomain)` assure que la variable globale possède son propre stockage dans chaque domaine d'application créé pour cette application.

Il existe des limitations à l’utilisation combinée par processus et par appdomain variables ; consultez [processus](../cpp/process.md) pour plus d’informations.

Par exemple, au lancement du programme, toutes les variables par processus sont initialisées, puis toutes les variables par domaine d'application. Par conséquent, lorsqu'une variable par processus est en cours d'initialisation, elle ne peut pas dépendre de la valeur d'une quelconque variable par domaine d'application. Il n'est pas recommandé de combiner l'utilisation (assignation) de variables par processus et par domaine d'application.

Pour plus d’informations sur la façon d’appeler une fonction dans un domaine d’application spécifique, consultez [call_in_appdomain, fonction](../dotnet/call-in-appdomain-function.md).

## <a name="example"></a>Exemple

```cpp
// declspec_appdomain.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

class CGlobal {
public:
   CGlobal(bool bProcess) {
      Counter = 10;
      m_bProcess = bProcess;
      Console::WriteLine("__declspec({0}) CGlobal::CGlobal constructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   ~CGlobal() {
      Console::WriteLine("__declspec({0}) CGlobal::~CGlobal destructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   int Counter;

private:
   bool m_bProcess;
};

__declspec(process) CGlobal process_global = CGlobal(true);
__declspec(appdomain) CGlobal appdomain_global = CGlobal(false);

value class Functions {
public:
   static void change() {
      ++appdomain_global.Counter;
   }

   static void display() {
      Console::WriteLine("process_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         process_global.Counter);

      Console::WriteLine("appdomain_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         appdomain_global.Counter);
   }
};

int main() {
   AppDomain^ defaultDomain = AppDomain::CurrentDomain;
   AppDomain^ domain = AppDomain::CreateDomain("Domain 1");
   AppDomain^ domain2 = AppDomain::CreateDomain("Domain 2");
   CrossAppDomainDelegate^ changeDelegate = gcnew CrossAppDomainDelegate(&Functions::change);
   CrossAppDomainDelegate^ displayDelegate = gcnew CrossAppDomainDelegate(&Functions::display);

   // Print the initial values of appdomain_global in all appdomains.
   Console::WriteLine("Initial value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   // Changing the value of appdomain_global in the domain and domain2
   // appdomain_global value in "default" appdomain remain unchanged
   process_global.Counter = 20;
   domain->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);

   // Print values again
   Console::WriteLine("Changed value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   AppDomain::Unload(domain);
   AppDomain::Unload(domain2);
}
```

```Output
__declspec(process) CGlobal::CGlobal constructor
__declspec(appdomain) CGlobal::CGlobal constructor
Initial value
process_global value in appdomain 'declspec_appdomain.exe': 10
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 1': 10
appdomain_global value in appdomain 'Domain 1': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 2': 10
appdomain_global value in appdomain 'Domain 2': 10
Changed value
process_global value in appdomain 'declspec_appdomain.exe': 20
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
process_global value in appdomain 'Domain 1': 20
appdomain_global value in appdomain 'Domain 1': 11
process_global value in appdomain 'Domain 2': 20
appdomain_global value in appdomain 'Domain 2': 12
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(process) CGlobal::~CGlobal destructor
```

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)