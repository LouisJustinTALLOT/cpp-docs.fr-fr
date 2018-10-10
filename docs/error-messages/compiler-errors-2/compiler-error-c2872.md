---
title: Erreur du compilateur C2872 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4bdc67e13db11949371e2f9e3d8a205b146d701
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890112"
---
# <a name="compiler-error-c2872"></a>Erreur du compilateur C2872

«*symbole*' : symbole ambigu

Le compilateur ne peut pas déterminer quel symbole que vous faites référence. Plusieurs symboles avec le nom spécifié est dans la portée. Consultez les remarques qui suivent le message d’erreur pour les emplacements de fichier et les déclarations le compilateur a trouvé pour le symbole ambigu. Pour résoudre ce problème, vous pouvez qualifier entièrement le symbole ambigu à l’aide de son espace de noms, par exemple, `std::byte` ou `::byte`. Vous pouvez également utiliser un [alias d’espace de noms](../../cpp/namespaces-cpp.md#namespace_aliases) pour donner à un espace de noms inclus un nom court pratique à utiliser lors de la résolution des ambiguïtés pour les symboles dans votre code source.

C2872 peut se produire si un fichier d’en-tête inclut un [à l’aide de la directive](../../cpp/namespaces-cpp.md#using_directives), et un fichier d’en-tête suivant est inclus qui contient un type qui se trouve également dans l’espace de noms spécifié dans la `using` directive. Spécifiez un `using` directive uniquement une fois que toutes vos fichiers d’en-tête sont spécifiés avec `#include`.

C2872 peut se produire dans Visual Studio 2013 en raison d’un conflit entre la le `Windows::Foundation::Metadata::Platform` enum type et C++ / c++ / CX-défini `Platform` espace de noms. Pour contourner ce problème, procédez comme suit :

- Supprimez la clause « à l’aide d’espace de noms Windows::Foundation::Metadata » à partir des fichiers projet.

- Spécifiez le nom qualifié complet pour tout type qui est inclus dans cet espace de noms.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2872, car une référence ambiguë est effectuée pour une variable nommée `i`; deux variables portant le même nom sont dans la portée :

```cpp
// C2872.cpp
// compile with: cl /EHsc C2872.cpp
namespace A {
   int i;
}

using namespace A;
int i;
int main() {
   ::i++;   // ok, uses i from global namespace
   A::i++;   // ok, uses i from namespace A
   i++;   // C2872 ambiguous: ::i or A::i?
   // To fix this issue, use the fully qualified name
   // for the intended variable.
}
```