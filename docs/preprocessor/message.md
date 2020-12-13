---
description: 'En savoir plus sur : pragma de message'
title: message, pragma
ms.date: 08/29/2019
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: 82b8efa7e232c24402b7fb1cce0fd1e38ff8be29
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333383"
---
# <a name="message-pragma"></a>message, pragma

Envoie un littéral de chaîne à la sortie standard sans mettre fin à la compilation.

## <a name="syntax"></a>Syntaxe

> **#pragma message (** *chaîne de message* **)**

## <a name="remarks"></a>Notes

Le pragma **message** est généralement utilisé pour afficher des messages d’information au moment de la compilation.

Le paramètre *de chaîne de message* peut être une macro qui se développe en un littéral de chaîne et vous pouvez concaténer ces macros avec des littéraux de chaîne dans n’importe quelle combinaison.

Si vous utilisez une macro prédéfinie dans le pragma de **message** , la macro doit retourner une chaîne. Dans le cas contraire, vous devrez convertir la sortie de la macro en chaîne.

Le fragment de code suivant utilise le pragma **message** pour afficher des messages pendant la compilation :

```cpp
// pragma_directives_message1.cpp
// compile with: /LD
#if _M_IX86 >= 500
#pragma message("_M_IX86 >= 500")
#endif

#pragma message("")

#pragma message( "Compiling " __FILE__ )
#pragma message( "Last modified on " __TIMESTAMP__ )

#pragma message("")

// with line number
#define STRING2(x) #x
#define STRING(x) STRING2(x)

#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")

#pragma message("")
```

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
