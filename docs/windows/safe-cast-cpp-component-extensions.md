---
title: safe_cast (Extensions du composant C++) | Microsoft Docs
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
ms.openlocfilehash: 57f59aa201a60fb2cf118b31eb4be377cd246ece
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606382"
---
# <a name="safecast-c-component-extensions"></a>safe_cast (extensions du composant C++)
Le **safe_cast** opération retourne l’expression spécifiée en tant que type spécifié, en cas de réussite ; sinon, lève `InvalidCastException`.  
  
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
  
## <a name="windows-runtime"></a>Windows Runtime  
 **safe_cast** vous permet de modifier le type d’une expression spécifiée. Dans les situations où vous vous attendez une variable ou un paramètre soit convertible en un certain type, vous pouvez utiliser **safe_cast** sans un **try-catch** bloc pour détecter les erreurs de programmation pendant le développement. Pour plus d’informations, consultez [Casting (C++ / c++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
```  
  
### <a name="parameters"></a>Paramètres  
 *id de type*  
 Le type vers lequel convertir *expression* à. Handle vers un type référence ou valeur, type valeur ou référence de suivi à un type référence ou valeur.  
  
 *Expression*  
 Expression qui s'évalue en handle vers un type référence ou type valeur, type valeur ou référence de suivi vers un type référence ou valeur.  
  
### <a name="remarks"></a>Notes  
 **safe_cast** lève `InvalidCastException` si elle ne peut pas convertir *expression* au type spécifié par *id de type*. Pour intercepter `InvalidCastException`, spécifiez la [/EH (modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md) option de compilateur et utilisez un **try/catch** instruction.  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/ZW`  
  
### <a name="examples"></a>Exemples  
  
 L’exemple de code suivant montre comment utiliser **safe_cast** avec le Runtime de Windows.  
  
```cpp  
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
 **safe_cast** vous permet de modifier le type d’une expression et générer du code MSIL vérifiable.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
```  
  
### <a name="parameters"></a>Paramètres  
 *id de type*  
 Handle vers un type référence ou valeur, type valeur ou référence de suivi à un type référence ou valeur.  
  
 *Expression*  
 Expression qui s'évalue en handle vers un type référence ou type valeur, type valeur ou référence de suivi vers un type référence ou valeur.  
  
### <a name="remarks"></a>Notes  
 L’expression `safe_cast<` *id de type*`>(`*expression* `)` convertit l’expression d’opérande en un objet de type id de type.  
  
 Le compilateur accepte un [static_cast](../cpp/static-cast-operator.md) dans la plupart des endroits qu’il accepte un **safe_cast**.  Toutefois, **safe_cast** garantit la génération du code MSIL vérifiable, alors qu’un **static_cast** risque de produire le code MSIL non vérifiable.  Consultez [Code pur et vérifiable (C++ / c++ / CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) et [Peverify.exe (outil PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) pour plus d’informations sur le code vérifiable.  
  
 Comme **static_cast**, **safe_cast** appelle des conversions définies par l’utilisateur.  
  
 Pour plus d’informations sur les conversions, consultez [opérateurs de Casting](../cpp/casting-operators.md).  
  
 **safe_cast** ne s’applique pas une **const_cast** (caster un **const**).  
  
 **safe_cast** est dans l’espace de noms cli.  Consultez [plateforme, par défaut et espaces de noms cli](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) pour plus d’informations.  
  
 Pour plus d’informations sur **safe_cast**, consultez :  
  
-   [Les Casts de Style C avec /clr (C++ / c++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [Guide pratique pour utiliser safe_cast dans C++-CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  

### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/clr`  
  
### <a name="examples"></a>Exemples  
  
 Un exemple d’où le compilateur n’accepte pas un **static_cast** mais accepte une **safe_cast** casts entre types d’interface non liées.  Avec **safe_cast**, le compilateur n’émettra pas d’une erreur de conversion et effectue une vérification lors de l’exécution pour voir si le cast est possible  
  
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