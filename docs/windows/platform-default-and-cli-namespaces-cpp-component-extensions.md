---
title: La plateforme, par défaut et espaces de noms cli (C++ / c++ / CLI et c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: fb7c9135051d790a488775451e1d333ce69d3dda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598002"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>La plateforme, par défaut et espaces de noms cli (C++ / c++ / CLI et c++ / CX)

Un espace de noms qualifie les noms des éléments du langage afin que les noms n'entrent pas en conflit avec des noms sinon identiques ailleurs dans le code source. Par exemple, une collision de nom peut empêcher le compilateur de reconnaître [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md). Les espaces de noms sont utilisés par le compilateur mais ne sont pas conservés dans l'assembly compilé.

## <a name="all-runtimes"></a>Tous les runtimes

Visual Studio fournit un espace de noms par défaut pour votre projet lorsque vous créez le projet. Vous pouvez renommer manuellement l’espace de noms, même si en C / c++ / CX, le nom du fichier .winmd doit correspondre au nom de l’espace de noms racine.

## <a name="windows-runtime"></a>Windows Runtime

Pour plus d’informations, consultez [espaces de noms et visibilité de type (C++ / c++ / CX)](https://msdn.microsoft.com/library/windows/apps/hh969551.aspx).

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntaxe

```cpp
using namespace cli;
```

### <a name="remarks"></a>Notes

C++ / c++ / CLI prend en charge la **cli** espace de noms. Lors de la compilation avec `/clr`, le **à l’aide de** instruction dans la section syntaxe est implicite.

Les fonctionnalités de langage suivantes se trouvent dans le **cli** espace de noms :

- [Tableaux](../windows/arrays-cpp-component-extensions.md)

- [interior_ptr (C++-CLI)](../windows/interior-ptr-cpp-cli.md)

- [pin_ptr (C++-CLI)](../windows/pin-ptr-cpp-cli.md)

- [safe_cast](../windows/safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre qu’il est possible d’utiliser un symbole dans le **cli** espace de noms comme symbole défini par l’utilisateur dans votre code.  Toutefois, une fois que vous l’avez fait, vous devez qualifier explicitement ou implicitement de vos références à la **cli** élément de langage du même nom.

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

[Extensions de composants pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)