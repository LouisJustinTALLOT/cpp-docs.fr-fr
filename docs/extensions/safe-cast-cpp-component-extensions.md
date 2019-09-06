---
title: safe_cast (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 42e141caed720aa29cf918a2bdf69d9a2c4203dc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311932"
---
# <a name="safe_cast-ccli-and-ccx"></a>safe_cast (C++/CLI et C++/CX)

L’opération **safe_cast** retourne l’expression spécifiée en tant que type spécifié, en cas de réussite ; sinon, lève une exception `InvalidCastException`.

## <a name="all-runtimes"></a>Tous les runtimes

(Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)

### <a name="syntax"></a>Syntaxe

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Windows Runtime

**safe_cast** vous permet de modifier le type d’une expression spécifiée. Dans les situations où vous vous attendez à ce qu’une variable ou un paramètre soit convertible en un certain type, vous pouvez utiliser **safe_cast** sans bloc **try-catch** pour détecter les erreurs de programmation pendant le développement. Pour plus d’informations, consultez [Cast (C++/CX)](../cppcx/casting-c-cx.md).

### <a name="syntax"></a>Syntaxe

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Paramètres

*type-id*<br/>
Type vers lequel convertir une *expression*. Handle vers un type référence ou valeur, type valeur ou référence de suivi à un type référence ou valeur.

*expression*<br/>
Expression qui s'évalue en handle vers un type référence ou type valeur, type valeur ou référence de suivi vers un type référence ou valeur.

### <a name="remarks"></a>Notes

**safe_cast** lève une exception `InvalidCastException` la conversion de l’*expression* dans le type spécifié par *type-id* n’est pas possible. Pour intercepter `InvalidCastException`, spécifiez l’option du compilateur [/EH (Modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md) et utilisez une instruction **try/catch**.

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

### <a name="examples"></a>Exemples

L’exemple de code suivant présente comment utiliser **safe_cast** avec Windows Runtime.

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

```Output
Caught expected exception: InvalidCastException
```

## <a name="common-language-runtime"></a>Common Language Runtime

**safe_cast** vous permet de modifier le type d’une expression et de générer du code MSIL vérifiable.

### <a name="syntax"></a>Syntaxe

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Paramètres

*type-id*<br/>
Handle vers un type référence ou valeur, type valeur ou référence de suivi à un type référence ou valeur.

*expression*<br/>
Expression qui s'évalue en handle vers un type référence ou type valeur, type valeur ou référence de suivi vers un type référence ou valeur.

### <a name="remarks"></a>Notes

L’expression `safe_cast<`*type-id*`>(`*expression*`)` convertit l’*expression* d’opérande en objet de type *type-id*.

Le compilateur accepte un [static_cast](../cpp/static-cast-operator.md) à la plupart des emplacements auxquels il accepte un **safe_cast**.  Toutefois, **safe_cast** garantit la production de code MSIL vérifiable, alors qu’un **static_cast** peut produire du code MSIL non vérifiable.  Voir [Code pur et vérifiable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) et [Peverify.exe (Outil PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) pour plus d’informations sur le code vérifiable.

À l’instar de **static_cast**, **safe_cast** invoque des conversions définies par l’utilisateur.

Pour plus d’informations sur les casts, consultez [Opérateurs de casting](../cpp/casting-operators.md).

**safe_cast** n’applique pas de **const_cast** (rejet de **const**).

**safe_cast** est dans l’espace de noms cli.  Consultez [Plateforme, valeur par défaut et espaces de noms cli](platform-default-and-cli-namespaces-cpp-component-extensions.md) pour plus d’informations.

Pour plus d’informations sur **safe_cast**, consultez :

- [Casts de style C avec /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)

- [Guide pratique : utiliser safe_cast dans C++/CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

Les casts entre types d’interface non liés constituent un exemple où le compilateur n’accepte pas un **static_cast** mais accepte un **safe_cast**.  Avec **safe_cast**, le compilateur n’émet pas d’erreur de conversion et effectue une vérification au moment de l’exécution si le cast est possible.

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

```Output
Caught expected exception
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)
