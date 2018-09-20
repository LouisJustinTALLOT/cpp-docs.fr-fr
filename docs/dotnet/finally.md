---
title: Pour finir | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 818ee6736d51303b047cb5a47aae02441557db29
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447275"
---
# <a name="finally"></a>finally

En plus de `try` et `catch` clauses, prend en charge des exceptions CLR un `finally` clause. La sémantique est identique à la `__finally` bloquer dans structurée des exceptions (SEH). Un `__finally` bloc peut suivre un `try` ou `catch` bloc.

## <a name="remarks"></a>Notes

L’objectif de la `finally` bloc consiste à nettoyer les ressources qui restent après l’exception s’est produite. Notez que le `finally` bloc est toujours exécuté, même si aucune exception n’a été levée. Le `catch` bloc est exécuté uniquement si une exception managée est levée dans associé `try` bloc.

`finally` est un mot clé contextuel ; consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant montre une simple `finally` bloc :

```
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

[Gestion des exceptions](../windows/exception-handling-cpp-component-extensions.md)