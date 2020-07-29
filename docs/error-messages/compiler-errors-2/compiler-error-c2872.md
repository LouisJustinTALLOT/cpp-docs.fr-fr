---
title: Erreur du compilateur C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: f57b250f87bd7f2c5808b5a681ddfe49dfa5e876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228893"
---
# <a name="compiler-error-c2872"></a>Erreur du compilateur C2872

'*symbol*' : symbole ambigu

Le compilateur ne peut pas déterminer le symbole auquel vous faites référence. Plusieurs symboles portant le nom spécifié sont dans la portée. Consultez les remarques qui suivent le message d’erreur pour les emplacements de fichiers et les déclarations que le compilateur a trouvé pour le symbole ambigu. Pour résoudre ce problème, vous pouvez qualifier complètement le symbole ambigu à l’aide de son espace de noms, par exemple `std::byte` ou `::byte` . Vous pouvez également utiliser un [alias d’espace de noms](../../cpp/namespaces-cpp.md#namespace_aliases) pour attribuer à un espace de noms inclus un nom abrégé pratique à utiliser lors de la disambiguating des symboles dans votre code source.

C2872 peut se produire si un fichier d’en-tête inclut une [directive using](../../cpp/namespaces-cpp.md#using_directives)et qu’un fichier d’en-tête suivant est inclus et qu’il contient un type qui se trouve également dans l’espace de noms spécifié dans la **`using`** directive. Spécifiez une **`using`** directive uniquement une fois que tous vos fichiers d’en-tête sont spécifiés avec `#include` .

C2872 peut se produire dans Visual Studio 2013 en raison d’un conflit entre le `Windows::Foundation::Metadata::Platform` type enum et l' `Platform` espace de noms C++/CX-defined. Pour contourner ce problème, procédez comme suit :

- Supprimez la clause « utilisation de l’espace de noms Windows :: Foundation :: Metadata » des fichiers projet.

- Spécifiez le nom qualifié complet de tout type inclus dans cet espace de noms.

## <a name="example"></a>Exemple

L’exemple suivant génère C2872, car une référence ambiguë est apportée à une variable nommée `i` ; deux variables portant le même nom se trouvent dans la portée :

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
