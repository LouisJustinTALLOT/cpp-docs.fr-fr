---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 2574ba5a10bbf5eddc68d6e0265d5dfc99c6d8fc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988336"
---
# <a name="finally"></a>finally

Outre les clauses `try` et `catch`, la gestion des exceptions CLR prend en charge une clause `finally`. La sémantique est identique au bloc `__finally` dans la gestion structurée des exceptions (SEH). Un bloc de `__finally` peut suivre un bloc `try` ou `catch`.

## <a name="remarks"></a>Notes

L’objectif du bloc `finally` est de nettoyer toutes les ressources restantes après l’exception. Notez que le bloc `finally` est toujours exécuté, même si aucune exception n’a été levée. Le bloc `catch` est exécuté uniquement si une exception managée est levée dans le bloc `try` associé.

`finally` est un mot clé contextuel ; Pour plus d’informations, consultez [Mots clés contextuels](../extensions/context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant illustre un bloc de `finally` simple :

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
