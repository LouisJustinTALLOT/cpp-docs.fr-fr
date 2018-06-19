---
title: safe_cast (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
dev_langs:
- C++
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c889d39df4d900beba5c9b41015e62293fdbbcde
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891514"
---
# <a name="safecast-c-component-extensions"></a>safe_cast (extensions du composant C++)
L'opération `safe_cast` retourne l'expression spécifiée en tant que type spécifié, en cas de réussite ; sinon, lève une exception `InvalidCastException`.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 (Aucune remarque pour cette fonctionnalité de langage ne s'applique à tous les runtimes.)  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Paramètres  
  
### <a name="remarks"></a>Notes  
  
## <a name="windows-runtime"></a>Windows Runtime  
 `safe_cast` vous permet de modifier le type d'une expression spécifiée. Dans les situations où vous vous attendez à ce qu'une variable ou un paramètre soit convertible en un certain type, vous pouvez utiliser safe_cast sans bloc try-catch pour détecter les erreurs de programmation pendant le développement. Pour plus d’informations, consultez [cast (C + c++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Paramètres  
 *id du type*  
 Le type vers lequel convertir *expression* à. Handle vers un type référence ou valeur, type valeur ou référence de suivi à un type référence ou valeur.  
  
 *expression*  
 Expression qui s'évalue en handle vers un type référence ou type valeur, type valeur ou référence de suivi vers un type référence ou valeur.  
  
### <a name="remarks"></a>Notes  
 `safe_cast` lève `InvalidCastException` si elle ne peut pas convertir *expression* pour le type spécifié par *id de type*. Pour intercepter `InvalidCastException`, spécifiez la [/EH (modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md) option du compilateur et l’utilisation d’une instruction try/catch.  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 L’exemple de code suivant montre comment utiliser `safe_cast` avec Windows Runtime.  
  
```cpp#  
// safe_cast_ZW.cpp  
// compile with: /ZW /EHsc  
  
using namespace default;  
using namespace Platform;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main(Array<String^>^ args) {  
   I1^ i1 = ref new X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.  
   }   
   catch(InvalidCastException^ ic) {  
     wprintf(L"Caught expected exception: %s\n", ic->Message);  
   }  
}  
```  
  
 **Sortie**  
  
```Output  
Caught expected exception: InvalidCastException  
```  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 `safe_cast` vous permet de modifier le type d'une expression et de générer du code MSIL vérifiable.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Paramètres  
 *id du type*  
 Handle vers un type référence ou valeur, type valeur ou référence de suivi à un type référence ou valeur.  
  
 *expression*  
 Expression qui s'évalue en handle vers un type référence ou type valeur, type valeur ou référence de suivi vers un type référence ou valeur.  
  
### <a name="remarks"></a>Notes  
 L’expression `safe_cast<` *id de type*`>(`*expression* `)` convertit l’expression d’opérande en objet de type id de type.  
  
 Le compilateur accepte un [static_cast](../cpp/static-cast-operator.md) dans la plupart des cas il n’acceptera une `safe_cast`.  Toutefois, `safe_cast` garantit la production de code MSIL vérifiable, alors qu'un `static_cast` peut produire du code MSIL non vérifiable.  Consultez [Code pur et vérifiable (C + c++ / CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) et [Peverify.exe (outil PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) pour plus d’informations sur le code vérifiable.  
  
 Comme `static_cast`, `safe_cast` appelle des conversions définies par l'utilisateur.  
  
 Pour plus d’informations sur les casts, consultez [opérateurs de Casting](../cpp/casting-operators.md).  
  
 `safe_cast` ne s’applique pas une **const_cast** (caster **const**).  
  
 `safe_cast` est dans l'espace de noms cli.  Consultez [plateforme, par défaut et espaces de noms cli](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) pour plus d’informations.  
  
 Pour plus d’informations sur **safe_cas**t, consultez :  
  
-   [Les Casts de Style C avec /clr (C + c++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [Guide pratique pour utiliser safe_cast dans C++-CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  

### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 Les casts entre types d'interface non liés constituent un exemple où le compilateur n'accepte pas un `static_cast` mais accepte un `safe_cast`.  Avec `safe_cast`, le compilateur n'émet pas d'erreur de conversion et effectue une vérification au moment de l'exécution si le cast est possible.  
  
```cpp  
// safe_cast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main() {  
   I1^ i1 = gcnew X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type  
   }   
   catch(InvalidCastException^) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 **Sortie**  
  
```Output  
Caught expected exception  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)