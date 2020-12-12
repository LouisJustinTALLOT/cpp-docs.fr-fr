---
description: 'En savoir plus sur : finally'
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 039c3fab7854d045c9b4917d2a0bc9f01fdc61a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252153"
---
# <a name="finally"></a>finally

En plus des **`try`** **`catch`** clauses et, la gestion des exceptions CLR prend en charge une **`finally`** clause. La sémantique est identique à celle du **`__finally`** bloc dans la gestion structurée des exceptions (SEH). Un **`__finally`** bloc peut suivre un **`try`** **`catch`** bloc ou.

## <a name="remarks"></a>Notes

L’objectif du **`finally`** bloc est de nettoyer toutes les ressources restantes après l’exception. Notez que le **`finally`** bloc est toujours exécuté, même si aucune exception n’a été levée. Le **`catch`** bloc est exécuté uniquement si une exception managée est levée dans le **`try`** bloc associé.

`finally` est un mot clé contextuel ; Pour plus d’informations, consultez [Mots clés contextuels](../extensions/context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant illustre un **`finally`** bloc simple :

```cpp
// keyword__finally.cpp
// compile with: /clr
using namespace System;

ref class MyException: public System::Exception{};

void ThrowMyException() {
   throw gcnew MyException;
}

int main() {
   try {
      ThrowMyException();
   }
   catch ( MyException^ e ) {
      Console::WriteLine(  "in catch" );
      Console::WriteLine( e->GetType() );
   }
   finally {
      Console::WriteLine(  "in finally" );
   }
}
```

```Output
in catch
MyException
in finally
```

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../extensions/exception-handling-cpp-component-extensions.md)
