---
title: Avertissement des outils Éditeur de liens LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7ac3ef2b6ad8f05a454dafe5e6a7ea0abc07a066
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685487"
---
# <a name="linker-tools-warning-lnk4227"></a>Avertissement des outils Éditeur de liens LNK4227

> Avertissement de l’opération de métadonnées (*HRESULT*) : *warning_message*

L’éditeur de liens a détecté des différences de métadonnées lors de la fusion :

- Un ou plusieurs assemblys référencés avec l’assembly en cours de génération.

- Un ou plusieurs fichiers de code source dans une compilation.

Par exemple, LNK4227 peut être provoquée si vous avez deux fonctions globales avec le même nom, mais que les informations sur les paramètres ont été déclarées différemment (autrement dit, les déclarations ne sont pas cohérentes dans tous les compilands). Utilisez ildasm.exe *object_file* /Text/Metadata sur chaque fichier. obj pour voir les différences entre les types.

LNK4227 est également utilisé pour signaler les problèmes qui proviennent d’un autre outil. Recherchez le message d’avertissement pour plus d’informations.

Les problèmes de métadonnées doivent être résolus pour résoudre l’avertissement.

## <a name="examples"></a>Exemples

LNK4227 est généré lorsqu’un assembly référencé a été signé différemment de l’assembly qui le référence.

L’exemple suivant génère l’LNK4227 :

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

Et puis

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

LNK4227 peut également être généré lorsque des numéros de version dans un format incorrect sont passés aux attributs d’assembly.  La notation' * 'est spécifique au `AssemblyVersionAttribute` .  Pour résoudre cet avertissement, utilisez uniquement des nombres dans les attributs de version autres que `AssemblyVersionAttribute` .

L’exemple suivant génère l’LNK4227 :

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
