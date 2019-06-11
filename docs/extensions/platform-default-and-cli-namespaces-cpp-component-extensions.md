---
title: Plateforme, valeur par défaut et espaces de noms cli (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: a7599e2987d27626e6f5c9d049d9a3bd4509c3ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516514"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Plateforme, valeur par défaut et espaces de noms cli (C++/CLI et C++/CX)

Un espace de noms qualifie les noms des éléments du langage afin que les noms n'entrent pas en conflit avec des noms sinon identiques ailleurs dans le code source. Par exemple, une collision de nom risque d’empêcher le compilateur de reconnaître des [mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md). Les espaces de noms sont utilisés par le compilateur mais ne sont pas conservés dans l'assembly compilé.

## <a name="all-runtimes"></a>Tous les runtimes

Visual Studio offre un espace de noms par défaut pour votre projet lorsque vous créez le projet. Vous pouvez renommer manuellement l’espace de noms, même si, dans C++/CX, le nom du fichier de .winmd doit correspondre au nom de l’espace de noms racine.

## <a name="windows-runtime"></a>Windows Runtime

Pour plus d’informations, consultez [Espaces de noms et visibilité de type (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh969551.aspx).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntaxe

```cpp
using namespace cli;
```

### <a name="remarks"></a>Remarques

C++/CLI prend en charge l’espace de noms **cli**. Lors de la compilation avec `/clr`, l’instruction **using** de la section Syntaxe est implicite.

Les fonctionnalités de langage suivantes se trouvent dans l’espace de noms **cli** :

- [Tableaux](arrays-cpp-component-extensions.md)

- [interior_ptr (C++-CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++-CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre qu’il est possible d’utiliser un symbole dans l’espace de noms **cli** comme symbole défini par l’utilisateur dans votre code.  Toutefois, une fois que vous l’avez fait, vous devez qualifier explicitement ou implicitement vos références à l’élément de langage **cli** du même nom.

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)